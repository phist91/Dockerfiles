# Dockerfile for a Docker image providing a base for a Gitlab runner container.

FROM debian:latest
LABEL maintainer="p.st@wwu.de"

# upgrade installed packages
RUN apt-get update \
    && apt-get dist-upgrade -y \
    && rm -rf /var/lib/apt/lists/*

# install wget, curl, cron and ca-certificates
RUN apt-get update \
    && apt-get install -y wget curl cron ca-certificates \
    && rm -rf /var/lib/apt/lists/* \
    && update-ca-certificates

# install gitlab runner
RUN apt-get update \
    && curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | bash \
    && apt-get install -y gitlab-runner \
    && rm -rf /var/lib/apt/lists/* \
    && (crontab -l 2>/dev/null; echo "@reboot gitlab-runner start") | crontab -

VOLUME /dockershare
CMD gitlab-runner start && bash
