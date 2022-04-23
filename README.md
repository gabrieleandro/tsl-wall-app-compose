# TSL Wall App

A TSL - Hiring Assignments project.

## Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)


## Setup

- [Installation](#installation)
- [Environment variables](#environment-variables)
- [Usage](#usage)
- [Test](#test)
- [Requirements](#requirements)


## Steps

Clone this repo.
```bash
git clone git@github.com:gabrieleandro/tsl-wall-app-compose.git
cd tsl-wall-app-compose
```

Clone the frontend and backend repos.
```bash
git clone git@github.com:gabrieleandro/tsl-wall-app-frontend.git
git clone git@github.com:gabrieleandro/tsl-wall-app-backend.git
```

## Environment
Create a .env file with

Backend env file.

```env
POSTGRES_NAME=
POSTGRES_USER=
POSTGRES_PASSWORD=

DEBUG=
SECRET_KEY=
ALLOWED_HOSTS=

CORS_ORIGIN_WHITELIST=

DEFAULT_FROM_EMAIL=
EMAIL_BACKEND=
SENDGRID_API_KEY=
```

Frontend env file.

```env
REACT_APP_API_BASE_URL=http://localhost:8000/api
REACT_APP_COOKIE_NAME=tslwallapp.token
```

## Build with docker compose

```bash
docker-compose build
docker-compose up -d
```

Visiti http://127.0.0.1:8000
