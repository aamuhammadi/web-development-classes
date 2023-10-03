Today we have discussed the following topic:

Advanced: Configuring Controllers and GraphQL APIs in Strapi

Kindly find the video link below:
https://drive.google.com/file/d/1E7GVeJ-IaRF9rficzLEzJcmJlE8_0eG0/view?usp=sharing

Helper code:
module.exports = {
routes: [
{
method: "GET",
path: "/news-articles/:url",
handler: "news.findOne",
config: {
auth: false,
},
},
],
};

"use strict";

/\*\*

- news controller
  \*/

const { createCoreController } = require("@strapi/strapi").factories;

module.exports = createCoreController("api::news.news", ({ strapi }) => ({
async findOne(ctx) {
const { url } = ctx.params;
const entity = await strapi.db.query("api::news.news").findOne({
where: { url },
populate: { category: true, image: true },
});

    return this.transformResponse(entity);

},
}));

register({ strapi }) {
const extensionService = strapi.plugin("graphql").service("extension");

    // get news by URL
    extensionService.use(({ strapi }) => ({
      typeDefs: `
            type Query {
              news(url: String!): NewsEntityResponse
            }
          `,
      resolvers: {
        Query: {
          news: {
            resolve: async (parent, args, context) => {
              const { toEntityResponse } = strapi.service(
                "plugin::graphql.format"
              ).returnTypes;

              const data = await strapi.services["api::news.news"].find({
                filters: { url: args.url },
                populate: {
                  category: true,
                  image: true,
                },
              });

              const response = toEntityResponse(data.results[0]);

              return response;
            },
          },
        },
      },
    }));

},
