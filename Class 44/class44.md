Today we have discussed the following topics:

Bonus Tip: Creating a Separate File for Endpoints
Migrating from REST to GraphQL

Kindly find the video link below:
https://drive.google.com/file/d/1r8AH0knoykHS1wCHvvNqBvXmVyUD2ZRy/view?usp=sharing

Helpers code:

import { ApolloClient, InMemoryCache } from "@apollo/client";
import { GRAPHQL_URL } from "../constants/endPoints";

const client = new ApolloClient({
uri: GRAPHQL_URL,
cache: new InMemoryCache(),
});

export default client;

<ApolloProvider client={client}>
<app>
</ApolloProvider>

const QUERY_Name = gql`  {
      Query-detail
    }`;

const fetchQueryData = async () => {
try {
const { data } = await client.query({ query: QUERY_Name });
setData(data.collectionname);
} catch (error) {
console.error(error);
}
};

useEffect(() => {
fetchQueryData();
}, []);
