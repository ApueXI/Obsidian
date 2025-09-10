---
Created: 2025-06-23T18:48
---
# REST vs GraphQL Cheat Sheet

|   |   |   |
|---|---|---|
|Aspect|REST|GraphQL|
|**Definition**|Architectural style using multiple endpoints (URLs)|Query language for APIs with a single endpoint|
|**Endpoint Structure**|Multiple URLs for different resources (e.g., `/users`, `/posts`)|Single endpoint (e.g., `/graphql`) for all queries and mutations|
|**Data Fetching**|Fixed response structure, often over-fetching or under-fetching|Client specifies exactly what data is needed in query|
|**Request Type**|Uses HTTP verbs: GET, POST, PUT, DELETE, PATCH|Uses POST requests with query/mutation in request body|
|**Versioning**|Usually needs versioning (e.g., `/v1/users`) when API changes|Versioning is typically avoided by evolving schema|
|**Over-fetching / Under-fetching**|Common problem (too much or too little data returned)|Solves by letting client specify fields exactly|
|**Learning Curve**|Simple, widely known, easy to cache|More complex, requires learning schema and query language|
|**Caching**|Easy to cache via HTTP caching mechanisms|Harder to cache because all queries are POST requests|
|**Error Handling**|HTTP status codes (404, 500, etc.) + error messages|Errors returned in response body alongside data|
|**Real-time Support**|Requires extra setup (WebSockets, SSE)|Built-in support via subscriptions|
|**Tooling**|Mature, lots of libraries and tools|Growing ecosystem, with powerful tools like GraphiQL and Apollo|
|**Flexibility**|Less flexible, server defines response shape|Very flexible, client controls data shape|
|**Use Cases**|Simple CRUD apps, public APIs, caching-heavy apps|Complex relational data, mobile apps, apps needing fewer requests|

  

## Summary

|   |   |
|---|---|
|REST|GraphQL|
|Multiple endpoints with fixed data per endpoint|Single endpoint, flexible queries|
|HTTP verbs (GET, POST, etc.) control actions|Query and mutation operations|
|Easier to cache with HTTP tools|Requires custom caching strategies|
|Over-fetching and under-fetching common|Client fetches exactly what it needs|
|Versioning needed for breaking changes|Schema evolves, minimizing versioning|
|Mature, simpler to implement|More powerful, but more complex|

  

## Example Requests

**REST:**

```Plain
GET /users/1
```

**Response:**

```JSON
{
  "id": 1,
  "name": "Alice",
  "posts": [/* posts data */]
}
```

  

**GraphQL:**

```GraphQL
query {
  user(id: 1) {
    id
    name
    posts {
      title
      publishedDate
    }
  }
}
```

**Response:**

```JSON
{
  "data": {
    "user": {
      "id": 1,
      "name": "Alice",
      "posts": [
        {
          "title": "Hello World",
          "publishedDate": "2023-01-01"
        }
      ]
    }
  }
}
```