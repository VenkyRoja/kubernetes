# Use of multi-stage builds in Docker file

- Multi-stage builds reduce the size of final image 
- creates a cleaner separation between the building of your image and the final output.
- splits Dockerfile instructions into distinct stages

With multi-stage builds, use multiple `FROM` statements in Dockerfile. Each `FROM` instruction can use a different base, and each of them begins a new stage of the build. Selectively copy artifacts from one stage to another as needed, leaving behind everything that is not needed in the final image.

#### Example

```
# syntax=docker/dockerfile:1
FROM ubuntu AS base
RUN echo "base"

FROM base AS stage1
RUN echo "stage1"

FROM base AS stage2
RUN echo "stage2"
```
#### Best practices
1. Choose the right base image
2. Rebuild your images often
```
docker build --no-cache -t my-image:my-tag .
```

Use the `--no-cache` option to avoid cache hits.

3. Exclude with `.dockerignore`
4. Create ephemeral containers

  Ephemeral means that the container can be stopped and destroyed, then rebuilt and replaced with an absolute minimum set up and configuration.

5. Don't install unnecessary packages
6. Decouple applications

Each container should have only one concern. Decoupling applications into multiple containers makes it easier to scale horizontally and reuse containers. For instance, a web application stack might consist of three separate containers, each with its own unique image, to manage the web application, database, and an in-memory cache in a decoupled manner.

7. Sort multi-line arguments

Example:
```
RUN apt-get update && apt-get install -y --no-install-recommends \
  bzr \
  cvs \
  git \
  mercurial \
  subversion \
  && rm -rf /var/lib/apt/lists/*
```
  
9. Leverage build cache
10. Pin base image versions
11. Build and test your images in CI

#### Docker file instructons

|        |         |             |
|--------|---------|-------------|
| FROM   | LABEL   | RUN         |
| CMD    | EXPOSE  | ENV         |
| ADD    | COPY    | ENTRYPOINT  |
| VOLUME | WORKDIR | ONBUILD     |

