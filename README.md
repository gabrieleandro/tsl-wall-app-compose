# TSL Wall App | Docker

A TSL - Hiring Assignment project built  with [Django](https://www.djangoproject.com/) and [Create React App](https://github.com/facebook/create-react-app).

Wall App is an application that allows users to register, login, and write on a wall.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment variables](#environment-variables)
- [Build with Docker Compose](#build-with-docker-compose)
- [Test](#test)

## Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Installation

Clone this repository.
```bash
git clone git@github.com:gabrieleandro/tsl-wall-app-compose.git tsl-wall-app
cd tsl-wall-app
```

Clone the Front-End and Back-End repositories.
```bash
git clone git@github.com:gabrieleandro/tsl-wall-app-frontend.git frontend
git clone git@github.com:gabrieleandro/tsl-wall-app-backend.git backend
```

## Environment variables
Create a .env file with

```env
DEBUG=
SECRET_KEY=
ALLOWED_HOSTS=

GUNICORN_WORKERS=5
GUNICORN_LOG_LEVEL=info
GUNICORN_TIMEOUT=60

CORS_ORIGIN_WHITELIST=

DEFAULT_FROM_EMAIL=
EMAIL_BACKEND=
SENDGRID_API_KEY=

REACT_APP_API_BASE_URL=
REACT_APP_COOKIE_NAME=
```

SECRET_KEY: You can generate a key, [here](https://djecrety.ir/).

In order to send emails using Sendgrid set:

```env
EMAIL_BACKEND=sendgrid_backend.SendgridBackend
```
SENDGRID_API_KEY: Create an API Key in Sendgrid, [here](https://app.sendgrid.com/settings/api_keys) .

## Build with Docker Compose

```bash
docker-compose -f docker-compose.yml build
docker-compose -f docker-compose.yml up -d
```

## Testing

Back-End tests

```bash
docker-compose -f docker-compose.yml run backend python manage.py test
```
