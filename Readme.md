An experimental, lightweight GraphQL wrapper for the [OpenCritic](https://opencritic.com/) API.

## Setup
```
npm install
npm start
```

The server will run on localhost:4000 by default

## Testing
There is one simple integration test that can be run with:
`npm run test`

## Info
The server uses [apollo-server](https://www.apollographql.com/docs/apollo-server/). It is run with [babel-node](https://babeljs.io/docs/en/babel-node) to support imports (for ease of organizing typedefs and resolvers) and runs with [nodemon](https://www.npmjs.com/package/nodemon).

The server uses [Apollo data sources](https://www.apollographql.com/docs/apollo-server/data/data-sources/) for fetching and deduplication. Running the server with `npm run debug` will log the OpenCritic API requests being made.

## Schema and Types
I didn't take the time to wrap the entire REST API, but through this endpoint you can:
- Search games by keyword
- Retrieve information about a game
- Get the review snippets and scores for each game

There are typedefs for the following fields from OpenCritic's API:
- Game
- Platform
- Review
- Outlet
- Author

## Example query
```
query {
    games(filter: "witcher 3") {
    id
    name
    Platforms {
      shortName
    }
    Reviews {
      snippet
      score
    }
  }
}
```

OpenCritic's Swagger docs can be found [here](https://app.swaggerhub.com/apis-docs/OpenCritic/OpenCritic-API/0.1.0#/).

