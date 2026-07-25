# QueryForge

A lightweight PostgreSQL query runner that provides a clean web interface to connect to PostgreSQL databases, execute SQL queries, and visualize results instantly.

## Overview

QueryForge is a full-stack SQL query execution platform inspired by database management tools like pgAdmin and DBeaver, but focused on a simple developer experience.

The application uses a connector-based backend architecture, making it easy to support multiple database providers in the future while currently implementing PostgreSQL.

## Features

- PostgreSQL datasource support
- Connector-based datasource architecture
- Execute SQL queries through REST APIs
- Interactive React dashboard
- Live tabular query results
- Error handling for invalid queries
- Modular backend built with NestJS
- Easily extendable for additional databases

## Tech Stack

### Backend

- NestJS
- TypeScript
- PostgreSQL
- node-postgres (pg)

### Frontend

- React
- TypeScript
- Vite
- Axios

## Architecture

```
queryforge
├── frontend
│   ├── React Dashboard
│   └── Query Editor
│
└── backend
    ├── Controllers
    ├── Services
    ├── Datasource Connectors
    │     └── PostgreSQL Connector
    └── Query Execution Engine
```

The backend follows a connector abstraction:

```
Datasource Connector
        │
        ▼
PostgreSQL Connector
        │
        ▼
Query Execution Service
        │
        ▼
REST API
        │
        ▼
React Dashboard
```

This design allows additional connectors (MySQL, MongoDB, SQLite, etc.) to be added without changing the API layer.

## API

### Execute Query

```
POST /query/execute
```

Request

```json
{
  "query": "SELECT * FROM users;"
}
```

Response

```json
{
  "columns": [
    "id",
    "name",
    "email"
  ],
  "rows": [
    {
      "id": 1,
      "name": "John",
      "email": "john@example.com"
    }
  ]
}
```

## Getting Started

### Clone

```bash
git clone https://github.com/yourusername/queryforge.git
cd queryforge
```

### Backend

```bash
cd backend
npm install
```

Create a `.env`

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=password
DB_NAME=queryforge
```

Run

```bash
npm run start:dev
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```


## Future Improvements

- Authentication
- Saved queries
- Query history
- Multiple datasource support
- Syntax highlighting
- Auto-complete
- Pagination for large datasets
- Export to CSV
- Query execution statistics
- Dark mode

## Learning Outcomes

This project helped explore:

- Backend architecture using NestJS
- Connector/Adapter design pattern
- PostgreSQL query execution
- REST API development
- React frontend integration
- Environment configuration
- End-to-end full-stack development

## License

MIT
