# Best Practice: Use of multi-stage builds in Docker file

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
