# Word Counter Deployment

This project facilitates the deployment of a service that allows users to upload a file, with the backend counting the frequency of each word within it. Additionally, it offers an API to download the uploaded file. The deployment is orchestrated using Docker Compose, which manages the instantiation of all required services.

## Setup

To get started, ensure you have Docker and Docker Compose installed on your system.

1. Clone this repository:
   ```bash
   git clone https://github.com/vnikhra/word-counter-deployment.git
   ```
2. Navigate into the cloned directory:
    ```bash
   cd word-counter-deployment
    ```
3. Before bringing up the services, add the following entry to your /etc/hosts file:
   ```bash
   127.0.0.1 host.docker.internal
   ```

## Services

The Docker Compose configuration in this repository orchestrates the following services:

- **Word Counter API**: [GitHub Repository](https://github.com/vnikhra/word-counter-api)
    - Provides endpoints for file upload and word frequency analysis.
- **Word Counter Worker**: [GitHub Repository](https://github.com/vnikhra/word-counter-worker)
    - Performs word frequency analysis asynchronously.
- **PostgreSQL**: Database service for storing application data.
- **RabbitMQ**: Message broker used for communication between the API and worker.
- **Minio**: Object storage service to mimic S3 for file uploads.

## Usage

To bring up all services, execute the following command from the project directory:

```bash
docker-compose up -d
```
The services will be built and started in the correct order.

## Client Application

For ease of interaction with the deployed server, you can use the **Word Counter Client** application available at [GitHub Repository](https://github.com/vnikhra/word-counter-client). This client allows you to connect to the server and upload files seamlessly.

## Notes

- Ensure that port `5050`, `5672`, `9000`, `9001`, `15432`, `15672` and `16666` are not occupied by other services on your system.
- Make sure to allocate sufficient resources to Docker to ensure smooth operation.
- Remember to remove the added entry from `/etc/hosts` once you're done with the deployment.

Happy analyzing! 📊✨
