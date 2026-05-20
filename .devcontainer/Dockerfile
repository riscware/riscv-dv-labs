# Use a lightweight base image just to handle authentication and pulling
FROM alpine:latest AS fetcher

# Declare the secret token provided by Codespaces
ARG GHCR_READ_TOKEN

# Log into GHCR and pull the private image layers locally
RUN apk add --no-cache docker-cli \
    && echo "${GHCR_READ_TOKEN}" | docker login ghcr.io -u token-user --password-stdin \
    && docker pull ghcr.io/riscware/cvw-docker:latest

# Build your final dev container using the layers pulled above
FROM ghcr.io/riscware/cvw-docker:latest
