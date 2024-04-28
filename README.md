## Description
This project is an API designed for distributed systems, providing JSON schema validation, token-based authentication, caching, and messaging using Redis, Elasticsearch, and RabbitMQ.

## Technology Stack
- Developed with Node.js and Express (JavaScript)
- Utilizes Redis for caching
- Employs Elasticsearch for indexing
- Utilizes RabbitMQ as the message broker

## Key Features
- Secure authentication using JWT-generated Bearer Tokens
- Validation of incoming JSON objects against their respective schemas
- Efficient caching and validation of cached responses using ETags
- Support for common HTTP methods like POST, PUT, PATCH, GET, and DELETE
- Persistent storage of JSON objects in Redis
- Indexing of JSON objects in Elasticsearch for efficient searching
- Asynchronous queuing of indexing requests to Elasticsearch via RabbitMQ

## Workflow
1. Obtain a token through the `/token` endpoint
2. Use the token for subsequent authenticated API requests
3. Create JSON objects via POST requests, ensuring validation against schemas
4. Redis stores hierarchical JSON objects after validation
5. Use RabbitMQ to enqueue objects for indexing in Elasticsearch
6. Dequeue objects from RabbitMQ and index them in Elasticsearch
7. Utilize Kibana Console to execute search queries on indexed data

## Setup Instructions
1. Install the required software:
    - Redis Server ([Download](https://redis.io/download))
    - Elasticsearch ([Download](https://www.elastic.co/downloads/elasticsearch))
    - Kibana ([Download](https://www.elastic.co/downloads/kibana))
    - RabbitMQ Server ([Download](https://www.rabbitmq.com/download.html))
2. Start Redis with `redis-server`
3. Start Elasticsearch with `elasticsearch`
4. Start Kibana with `kibana`
5. Start RabbitMQ with `rabbitmq-server`
6. Once servers are running, interact with the API endpoints to create and query data.

## API Endpoints
- `GET /token`: Generates a JWT token for authentication.
- `POST /plan`: Creates a new plan.
- `PUT /plan/{id}`: Updates an existing plan, requiring a valid Etag.
- `PATCH /plan/{id}`: Modifies an existing plan, requiring a valid Etag.
- `GET /plan/{id}`: Retrieves an existing plan, optionally with an Etag.
- `DELETE /plan/{id}`: Deletes an existing plan, requiring a valid Etag.
