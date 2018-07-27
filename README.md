# gql-mock-server

## This package is not maintained anymore. I would recommend you to use [apollo-server](https://github.com/apollographql/apollo-server) instead.

GraphQL server based on graphql-server-express, preconfigured with cors to be used as a mock server. You can find more info in [this medium post](https://medium.com/trabe/mocking-your-graphql-server-is-easier-with-gql-mock-server-9d72ce07a657).

## How to use

``` javascript
import gql from "gql-mock-server";

const types = `
type User {
  id: ID
  name: String
}

type Query {
  users: [User]
}
`;

const resolvers = {
  Query: {
    users: () => [{ id: "1", name: "Peter" }, { id: "2", name: "Frank" }]
  }
};

gql({ types, resolvers });
```

## API

The gql function accepts the following arguments:

```javascript
gql(
  schema, // schema object: { types, resolvers }
  {
    context, // context builder: request => ({})
    port, // server port: 3002
    endpoint, // endpoint for the gql server: "/graphql"
    verbose // default is true, if false is passed, will not console.log on start
  }
)
```
