# Dockerfile for a Docker image providing OpenJDK 11, Maven and GitLab Runner.

FROM phist91/gitlab-runner-base:latest
LABEL maintainer="p.st@wwu.de"

# Installing JDK 11 and Maven
RUN apt-get update -y \
    && apt-get install -y curl openjdk-11-jdk maven

