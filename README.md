Graphql API plus basic React web app

**API** Node + Express + GraphQL + Sequelize + Postgres

## Running
- Clone repo
- Install NPM modules API `cd api` and `yarn install`
- Install NPM modules Webapp `cd web` and `yarn install`
- Modify `/api/src/config/database.json`, add you local postgress connection info to 'development' setup (username, database name, port)

```
    "connection": "postgres://bryant:@localhost:5432/graphql_postgres"
```


- Start API `cd api` and `yarn start`
- (Optional) Start Webapp `cd web` and `yarn start` http://localhost:3000/



## Sample GraphQL Queries
### http://localhost:8005
```
query {
  thoughts {
    id,
    name,
    thought
  }
}
```
## Response
```
{
  "data": {
    "thoughts": [
      {
        "id": 1,
        "name": "Arya Stark",
        "thought": "A girl has no name"
      },
      {
        "id": 2,
        "name": "Jon Snow",
        "thought": "I know nothing"
      }
    ]
  }
}
```
```
query {
  thought(id: 1) {
    id,
    name,
    thought
  }
}
```
```
{
  "data": {
    "thought": {
      "id": 1,
      "name": "Arya",
      "thought": "A girl has no name"
    }
  }
}
```

```
mutation {
  thoughtCreate(
    name: "Tyrion Lannister", 
    thought:"I drink and I know things"
  ) {
    id
  }
}
```
```
{
  "data": {
    "thoughtCreate": {
      "id": 3
    }
  }
}
```
```
mutation {
  thoughtRemove(id: 3) {
    id
  }
}
```

```
{
  "data": {
    "thoughtRemove": {
      "id": null
    }
  }
}
```

## Source: https://github.com/atulmy/fullstack-graphql
