# Dockerfiles
https://github.com/phist91/Dockerfiles

1. [beckerbox](#beckerbox)
2. [maven-gitlab-runner](#maven-gitlab-runner)
3. [texlive-full-minted](#texlive-full-minted)
4. [texlive-gitlab-runner](#texlive-gitlab-runner)

## beckerbox
Jonas Becker's very own Docker container for testing purposes made for the project course "Geometriebasierte Entscheidungsunterstützung in der forensischen Chemometrie", winter semester 2019/20.

## maven-gitlab-runner
Dockerfile for a Docker image providing OpenJDK 11, Maven and GitLab Runner.
 
## texlive-full-minted
Dockerfile for a Docker image providing a full up-to-date TeX Live installation with minted package support (and therefore with Python and Pygments). Build may fail at times because of CTAN choosing a broken mirror.

## texlive-gitlab-runner
Dockerfile for a Docker image providing a full up-to-date TeX Live installation with minted package support (and therefore with Python and Pygments) and pre-installed GitLab Runner.