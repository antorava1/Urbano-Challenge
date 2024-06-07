# Admin Panel Project

## Assumptions

### User Roles

User can have only 1 role. There are 3 roles: Admin, Editor, User. Authorization permissions for each role are described below:

#### Admin

| Table    | Read | Write | Update | Delete |
|----------|------|-------|--------|--------|
| Users    | ✓    | ✓     | ✓      | ✓      |
| Courses  | ✓    | ✓     | ✓      | ✓      |
| Contents | ✓    | ✓     | ✓      | ✓      |

#### Editor

| Table    | Read     | Write | Update | Delete |
|----------|----------|-------|--------|--------|
| Users    | itself   |       |        |        |
| Courses  | ✓        | ✓     | ✓      |        |
| Contents | ✓        | ✓     | ✓      |        |

#### User

| Table    | Read   | Write | Update | Delete |
|----------|--------|-------|--------|--------|
| Users    | itself |       |        |        |
| Courses  | ✓      |       |        |        |
| Contents | ✓      |       |        |        |

## Tech Stack

- Backend: NestJS
- Frontend: React
- Database: PostgreSQL
- Testing: Jest for unit testing. Postman for e2e testing.

## Features

- Swagger Documentation
- JWT authentication with refresh & access token
- Role based authorization
- Data filtering
- Fully responsive design

## Authentication

Application generates 2 tokens on login: Access token and refresh token. Access token has a lifetime of 15 minutes and the refresh token has a lifetime of 1 year.

## First Login

On the first run, application inserts a new admin to the database.

- Username: admin
- Password: admin123

## How to Setup

### Deploy with Docker

You can run the entire app using docker compose.

1. On root directory:

```bash
docker-compose up -d
```

Application will be deployed on http://localhost:3000

Swagger Docs on http://localhost:3000/api/docs

### Running Locally

#### Backend

1. First, make sure you have PostgreSQL installed on your computer.

2. Edit the database properties on the backend/.env file.

3. On backend directory:

```bash
# Installing the dependencies
yarn

# Running the app
yarn start
```

Backend will be started on http://localhost:5000

Swagger Docs on http://localhost:5000/api/docs

#### Frontend

1. On frontend directory:

```bash
# Installing the dependencies
yarn

# Running the app
yarn start
```

Frontend will be started on http://localhost:3000

### Testing

#### Unit Testing

On backend directory:

```bash
yarn test
```

#### e2e API Testing

1. First, start the backend locally.

2. On backend directory:

```bash
# Install the dependencies
yarn

# Start the backend locally
yarn start
```

3. Start the test:

Test will login as username: admin, password: admin123 and create users with usernames test and test2. If you change username and password of admin or if you add users with username test and test2. Tests will fail.

```bash
yarn test:e2e
```
