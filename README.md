# SGBS Project Setup (Dockerized)

This guide instructions how to set up and run the SGBS (Sistema de Gestão de Banco de Sangue) project using Docker. This setup containerizes the Frontend, Backend, and Database for easy deployment.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed.
- [Docker Compose](https://docs.docker.com/compose/install/) installed.
- [Git](https://git-scm.com/downloads) installed.

## Installation

1.  **Prepare the directory**
    Ensure you have the following files in your working directory (root):
    - `docker-compose.yml`
    - `Dockerfile.frontend`
    - `Dockerfile.backend`
    - `.dockerignore`

2.  **Clone the repositories**
    Clone the Frontend and Backend repositories into this directory:

    ```bash
    git clone https://github.com/Pavulla/SGBS-Frontend.git
    git clone https://github.com/Pavulla/SGBS-Backend.git
    ```

    Your directory structure should look like this:
    ```
    .
    ├── docker-compose.yml
    ├── Dockerfile.frontend
    ├── Dockerfile.backend
    ├── .dockerignore
    ├── SGBS-Frontend/
    └── SGBS-Backend/
    ```

## Running the Application

Start the entire stack using Docker Compose:

```bash
docker-compose up -d
```

This command will:
1.  Start a MySQL 5.7 database container.
2.  Build and start the Backend container (port 3333).
3.  Build and start the Frontend container (port 3000).

*Note: The first run may take a few minutes to build the images.*

## Accessing the Services

- **Frontend**: http://localhost:3000
- **Backend API Docs (Swagger)**: http://localhost:3333/api-docs/
- **Backend API**: http://localhost:3333

## Troubleshooting

- **Database Connection**: The backend is automatically configured to connect to the Docker database host (`db`). Do not modify `config/config.json` manually if running via Docker.
- **Rebuild**: If you make changes to the Dockerfiles or need to refresh the build, run:
    ```bash
    docker-compose up -d --build
    ```
