# Docker Example: Langflow

This docker-compose example shows how to run Langflow with a Postgres database. The server is fully running and connected to a postgres database that's in the same docker network. Both backend and frontend are running in a single container.

### Setup


#### ⚠️ Prerequisites:

* [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/)
* [Make](https://www.gnu.org/software/make/) _(optional)_

1. Edit the `.env` file with your `LANGFLOW_DATABASE_URL` and other settings or environment variables.

```bash
cp docker.env .env
```

2. Run

    ```bash
    docker compose up
    ```

    Or if you prefer to use the pre-built image:
    ```bash
    docker compose -f pre.docker-compose.yml up
    ```

Langflow will be available at `http://localhost:7860/`.

### Development

This example is useful for development because it starts a postgres container and provides the connection string through environment variables.

> **Tip**: if you are developing Langflow locally, you can set the `LANGFLOW_DATABASE_URL` to `postgresql://langflow:langflow@localhost:5432/langflow` to use the same postgres container.
