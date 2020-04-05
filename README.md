# deploy-server

Server for deploying websites using nginx, lets encrypt and docker.

## API

The API is a `multipart/form-data` request to `PUT /{subdomain}`

- **container[image]** - which image should be used to create the container with
- **container[env][EXAMPLE_VAR]** - sets the `EXAMPLE_VAR` environment variable
- **static_files** - zip file containing static files to be served by nginx

## Static files take priority

Static files can be provided as a zip file. If a request matches a static file in this zip file then this will be served without querying the docker container.

This is to optimize for nginx's amazing static file performance and to offload the docker container.

## Docker containers are optional

Static sites are a first class citizen. It's totally okay to only serve static files and do nothing else.

## Static files are optional

Including static files is only meant as a way to accelerate requests. You can still serve your static files from your docker container, if you prefer.

## Static files and containers can be combined

You can combine the two to effectively deploy JAMstack sites.
