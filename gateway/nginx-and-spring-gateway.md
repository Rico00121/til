# What are the differences and similarities between Nginx and Spring Gateway?

## API Gateway
A intermediate server used to aggregate, route and protect requests(by limiting current) from multiple backend services.

It's a high-level concept, including spring gateway and nginx.

### Core objectives
As a entry point between clients and backend services.

Provide an universal, security and controllable access entry.

## Similarities

Reverse proxy

API gateway

Request forwarding

Authority

## Differences

Nginx need to collabrate with other anth server (such as OAuth 2.0 server) to realize authentication and authority.

Nginx is realized by C and use ymal and json to config, Spring gateway is based on Java, which use @Annotation or config class.








