# Effective Mobile Project

This project implements a simple Python-based web application proxied through Nginx, all orchestrated using Docker Compose.

## Architecture Description

The application uses a two-tier architecture:
1.  **Nginx (Reverse Proxy):** Acts as the entry point for all requests. It listens on a configurable host port and forwards traffic to the backend service within the Docker network.
2.  **Backend (Python):** A lightweight HTTP server built with Python's standard `http.server` module. It serves a "Hello from Effective Mobile!" message.

## Interaction Diagram

```text
       +----------+          +-----------------------+          +----------------+
       |  Client  | -------->| Nginx (Reverse Proxy) | -------->| Python Backend |
       +----------+  Port 80 +-----------------------+ Port 8080+----------------+
```

## Technologies Used

- **Python 3.12**: Backend runtime (Alpine-based).
- **Nginx**: High-performance reverse proxy server.
- **Docker & Docker Compose**: Containerization and service orchestration.
- **Alpine Linux**: Minimalist base image for containers.

## Launch Instructions

To launch the project, follow these steps:

1.  **Clone the repository** (if not already done).
2.  **Set the Nginx port**:
    The `docker-compose.yml` uses an environment variable `NGINX_PORT` (defaulting to 80 if not set). You can create a `.env` file from the example:
    ```bash
    cp .env.example .env
    ```
    Or simply rely on the default value.
3.  **Start the containers**:
    Run the following command in the project root:
    ```bash
    docker compose up --build -d
    ```

## Functionality Check

Once the containers are running, you can verify the application is working by sending a request to the configured port:

```bash
curl http://localhost:80
```

Expected output:
```text
Hello from Effective Mobile!
```
