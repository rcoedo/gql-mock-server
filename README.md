# gql-mock-server

GraphQL server based on graphql-server-express, preconfigured with cors to be used as a mock server

## How to use

```
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

```
gql(
  schema, // schema object: { types, resolvers }
  {
    context, // context builder: request => ({})
    port, // server port: 3002
    endpoint, // endpoint for the gql server: "/graphql"
  }
)
```
