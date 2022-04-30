# TSL Wall App | Docker

A TSL - Hiring Assignment project built  with [Django](https://www.djangoproject.com/) and [Create React App](https://github.com/facebook/create-react-app).

Wall App is an application that allows users to register, login, and write on a wall.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment variables](#environment-variables)
- [Observations](#observations)
- [Build with Docker Compose](#build-with-docker-compose)
- [Testing](#testing)

## Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

# Installation

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

Make sure you have the following directories tree:

```bash
.
├── backend
├── frontend
├── docker-compose-test.yml
├── docker-compose.yml
├── .env.example
├── .env
└── README.md
```

# Environment variables

Copy our .env.example file (included in this repo)

```bash
cp .env.example .env
```

or create a .env file with 

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

## Observations
The welcome email will be printed on the console.

The default EMAIL_BACKEND is using django.core.mail.backends.console.EmailBackend.

Instead of sending out real emails the console backend just writes the emails that would be sent to the standard output [more info](https://docs.djangoproject.com/en/4.0/topics/email/#console-backend).

### In order to send emails using Sendgrid:
Create an API Key in Sendgrid, [here](https://app.sendgrid.com/settings/api_keys).
And set the EMAIL_BACKEND to 
```bash
EMAIL_BACKEND=sendgrid_backend.SendgridBackend
```

# Build with Docker Compose

```bash
docker-compose -f docker-compose.yml build
docker-compose -f docker-compose.yml up -d
```

Now you can access the backend at http://localhost:8000/

and the frontend at http://localhost:3000/

# Testing

#### Back-End tests

Make sure you run the previous commands and the containers are up.

Run the tests using the following command:

Run the tests using the following command:

```bash
docker-compose -f docker-compose.yml run backend python manage.py test
```

#### Front-End tests

Run docker-compose up in order to recreate the frontend container with the tests env from docker-compose-test and wait to start.

```bash
docker-compose -f docker-compose.yml -f docker-compose-test.yml up -d
docker-compose -f docker-compose.yml -f docker-compose-test.yml run test