Today we have discussed the following topics:

Migrating from REST to GraphQL
Understanding mutation query

Kindly find the video link below:
https://drive.google.com/file/d/1ZFLB-Ibze67-hJsK2BV6aXHm-RlZoNM8/view?usp=sharing

Helpers code:

const { data } = await client.mutate({
mutation: MUTATION_NAME,
variables: {
data: DATA
},
});
