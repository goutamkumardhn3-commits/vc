# To-Do App — React + Node + GraphQL

A full-stack to-do list app:
- **Server**: Node.js, Express, Apollo Server (GraphQL API, in-memory data store)
- **Client**: React, Apollo Client

## Features
- Add, edit (double-click a task), toggle complete, and delete todos
- Filter by All / Active / Completed
- Clear all completed todos
- Optimistic UI update when toggling completion

## Project structure
```
todo-app/
  server/         GraphQL API (Express + Apollo Server)
    index.js
    schema.js
    resolvers.js
    package.json
  client/         React frontend (Apollo Client)
    public/index.html
    src/
      App.js
      App.css
      apolloClient.js
      queries.js
      index.js
    package.json
```

## Running it

### 1. Start the GraphQL server
```bash
cd server
npm install
npm start
```
Server runs at `http://localhost:4000/graphql`.

### 2. Start the React client
In a new terminal:
```bash
cd client
npm install
npm start
```
App opens at `http://localhost:3000`.

The client is configured (in `apolloClient.js`) to talk to `http://localhost:4000/graphql` by default. Override with an environment variable if needed:
```bash
REACT_APP_GRAPHQL_URL=http://localhost:5000/graphql npm start
```

## Notes on going to production
- Data is stored **in memory** on the server and resets on restart — swap the array in `resolvers.js` for a real database (e.g. Postgres, MongoDB) for persistence.
- Add authentication/authorization if todos should be per-user.
- Update `CLIENT_ORIGIN` in `server/index.js`'s CORS config to match your deployed client's URL.
