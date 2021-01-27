
# Tools for generating GraphQL schema

**Important resourses to read more**
https://github.com/hasura/sphinx-graphiql  
https://hasura.io/docs/1.0/graphql/core/schema/export-graphql-schema.html  
https://github.com/hasura/graphqurl  
https://github.com/prisma-labs/get-graphql-schema  
https://github.com/apollographql/apollo-tooling  

If you need to share, introspect or export the GraphQL schema, you can use community tooling such as:
-   [graphqurl](https://github.com/hasura/graphqurl)
-   [Apollo CLI](https://github.com/apollographql/apollo-tooling)
-   [get-graphql-schema](https://github.com/prisma-labs/get-graphql-schema)
    

## Using **graphqurl**

Install graphqurl:

```
npm install -g graphqurl
```

Then you can run the following commands to download the GraphQL schema:

```
# If the GraphQL engine is running at https://my-graphql-engine.com/v1/graphql without an admin secret
gq https://my-graphql-engine.com/v1/graphql --introspect > schema.graphql

# If Hasura GraphQL engine is running with an admin secret
gq https://my-graphql-engine.com/v1/graphql -H "X-Hasura-Admin-Secret: adminsecretkey" --introspect > schema.graphql
```

By default, it downloads the schema in .graphql format:

```
gq https://my-graphql-engine.com/v1/graphql --introspect > schema.graphql
```

If you want it in JSON format, you can use an additional flag --format json:

```
gq https://my-graphql-engine.com/v1/graphql --introspect --format json > schema.json
```

## Using **get-graphql-schema**

Install the get-graphql-schema

```
npm install -g get-graphql-schema
```
Fetch GraphQL schema from a GraphQL HTTP endpoint

```
# Getting the schema in .graphql format
get-graphql-schema https://my-graphql-engine.com/v1/graphql > schema.graphql

# Getting the schema in .json format
get-graphql-schema --json https://my-graphql-engine.com/v1/graphql > schema.json
```

## Using **Apollo CLI**

Install the Apollo CLI:

```
npm install -g apollo
```

You can then run the following commands to download the GraphQL schema:

```
# If the GraphQL engine is running at https://my-graphql-engine.com/v1/graphql,
# without an admin secret
apollo schema:download --endpoint https://my-graphql-engine.com/v1/graphql

# If Hasura GraphQL engine is running with an admin secret
apollo schema:download --endpoint https://my-graphql-engine.com/v1/graphql --header "X-Hasura-Admin-Secret: adminsecretkey"
```
Note that apollo schema:download is an [alias of the command](https://github.com/apollographql/apollo-tooling#apollo-servicedownload-output) apollo service:download.  
By default, this downloads the schema to a file called schema.json. This command has no other output types.  
