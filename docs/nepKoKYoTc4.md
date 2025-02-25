---
layout: default
title: Making PostgreSQL + Django run directly from g-repo
category: Cryptography
tags: [Cryptography]

---

how to run a full Django + PostgreSQL development environment in GitHub Codespaces, configured so anyone else who creates a Codespace from that repository will get a working environment.

So, in my project's .devcontainer directory, I need:

a) devcontainer.json
```
{
  "dockerComposeFile": "docker-compose.yml",
  "service": "app",
  "waitFor": "onCreateCommand",
  "updateContentCommand": "",
  "postCreateCommand": "pip install --user -r requirements.txt && python manage.py collectstatic && python manage.py migrate",
  "postAttachCommand": {
    "server": "python manage.py runserver"
  },
  "containerEnv": {
    "DATABASE_URL": "postgres://postgres:postgres@db/pillarpointstewards"
  },
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-python.python"
      ]
    }
  },
  "portsAttributes": {
    "8000": {
      "label": "Application"
    }
  },
  "forwardPorts": [8000]
}
```
This references the docker-compose.yml file that we will define next, and specifies that the main service is the thing in that file that's defined in the app block.

I originally had "onAutoForward": "openPreview" in the "portsAttributes": {"8000"...} section - but this caused Codespaces to constantly attempt to open a preview window every time the Django server restarted (which was every time I typed code into a file and it auto-saved it) which was really annoying, especially since that "Simple Browser" window just showed me a Firefox error due to not wanting to embed my page in that iframe).

I haven't completely figured out the different commands, but the above recipe worked for me - where the postCreateCommand installs dependencies and runs migrations, and the postAttachCommand starts a development server.

Here's that postCreateCommand in full:

pip install --user -r requirements.txt \
  && python manage.py collectstatic \
  && python manage.py migrate
I'm installing requirements, running collectstatic (needed for my project that uses whitenoise) and then running migrations.

The containerEnv key holds environment variables. I'm telling it where to find PostgreSQL - my settings.py file then uses dj_database_url like this:

import dj_database_url

DATABASES = {}
DATABASES["default"] = dj_database_url.config()
The customizations key says that I want the VS Code Python extension.

The portsAttributes and forwardPorts pieces ensure port 8000 will be forwarded and made available for a browser tab inside the Codespaces environment.

2) docker-compose.yml
```
# This file exists to ensure the PostgreSQL server is running:

version: '3.8'

services:
  app:
    build:
      context: ..
      dockerfile: .devcontainer/Dockerfile

    volumes:
      - ../..:/workspaces:cached

    command: sleep infinity
    network_mode: service:db

  db:
    image: postgres:latest
    restart: unless-stopped
    volumes:
      - postgres-data:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: postgres
      POSTGRES_DB: pillarpointstewards
      POSTGRES_PASSWORD: postgres

volumes:
  postgres-data:
```
Note that setting POSTGRES_DB to pillarpointstewards caused a database of that name to be created when the server started.

3) DockerFile:
FROM mcr.microsoft.com/devcontainers/python:1-3.11-bullseye

ENV PYTHONUNBUFFERED 1

---
To run this codespace With this .devcontainer/ directory setup for a repository, starting a Codespace for it can be done from the green Code button menu:

---
Once it's finished starting up, there should be a Django development server running. To view that in your browser, click on the "Ports" tab and then hover over the development server and click the little globe icon:

The ports tab shows available ports, with their local addresses

This should open a new browser window that exposes the port-forwarded development server.

---
ALLOWED_HOSTS #
GitHub Codespaces assigns a random subdomain to your development environment every time you start it.

I found I needed to add this to settings.py:

ALLOWED_HOSTS = ["*"]
