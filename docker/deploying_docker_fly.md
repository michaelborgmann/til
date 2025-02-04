# Deploying with Docker on Fly.io

### Setup

Get and install [Docker](https://www.docker.com) if not already done.

#### Key Terms:

* **Container**: Virtualizes OS and hardware to run applications.
* **Image**: A bootable snapshot of a server with code, dependencies, and assets.

### Steps to Deploy:

1. Package the service into a Docker image.
2. Publish the image to a container registry.
3. Run the service in a container.

## Creating a Dockerfile

The `Dockerfile` defines how to build an image:

```
FROM node:23.7.0
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci
COPY ./src ./src
CMD npm start
```

### Optional: `.dockerignore

Exclude unnecessary files from the image:

```
touch .dockerignore
```

## Building and Running Locally

Build the image:

```
docker build -t docker-image-name --file Dockerfile .
```

Check built images:

```
docker image list
```

Run a container, detached (`-d`), bind container port to host (`-p`), and setting the `PORT` environment variable:

```
docker run -d -p 3000:3000 -e PORT=3000 docker-image-name
```

List running containers, including stopped ones:

```
docker container list
docker container list --all
```

Access logs:

```
docker logs <container-id>
```

Enter the container shell:

```
docker exec -it <container-id> bash
```

Stop and remove the container:

```
docker stop <container-id>
docker rm <container-id>
```

## Publishing to Fly.io

1. Install and set up [Fly.io](https://fly.io)
2. Launch the app: `fly launch`

Or manually create an app:

```
fly apps create my-docker-image
```

Tag the image:

```
docker build -t registry.fly.io/my-docker-image:v0.0.1 .
```

Authenticate and push the image:

```
fly auth docker
docker push registry.fly.io/my-docker-image:v0.0.1
```

Deploy the app:

```
fly deploy --app my-docker-image --image registry.fly.io/my-docker-image:v0.0.1
```

Visit: [https://my-docker-image.fly.dev](https://my-docker-image.fly.dev)

### Alternative Manual Deployment

Remove local container before running:

```
docker rmi <image-id> --force
```

Run the container from the registry:

```
docker run -d -p 3000:3000 -e PORT=3000 registry.fly.io/my-docker-image:v0.0.1
```

### Other Cloud Services

For Azure, AWS, or GCP, steps may include:

* **Login**: `docker login <registry-url> --username <user> --password <pass>`
* **Tag Image**: `docker tag <existing-image> <registry-url>/<image-name>:<version>`
