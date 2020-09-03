# Dockerfile for a Docker image providing a full up-to-date TeX Live
# installation with minted package support (and therefore with Python and
# Pygments) and pre-installed GitLab Runner.
# Build may fail at times because of CTAN choosing a broken mirror.

FROM phist91/gitlab-runner-base:latest
LABEL maintainer="p.st@wwu.de"

# Basic system and Python / Pygments setup
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y \
        perl \
        fontconfig \
        libwww-perl \
        python \
        python-pip \
        ghostscript \
    && pip install Pygments

# Installing TeX Live
COPY texlive-gitlab-runner/texlive.profile /
ARG TLSETUP_PATH=http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
RUN wget $TLSETUP_PATH \
    && tar xzvf install-tl-unx.tar.gz \
    && ./install-tl-*/install-tl -profile /texlive.profile \
    && rm -rf install-tl-* \
    && (crontab -l 2>/dev/null; echo "0 3 * * * tlmgr update --self --all --reinstall-forcibly-removed") | crontab -
