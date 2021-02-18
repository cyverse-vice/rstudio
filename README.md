[![Project Supported by CyVerse](https://img.shields.io/badge/Supported%20by-CyVerse-blue.svg)](https://learning.cyverse.org/projects/vice/en/latest/) [![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4540326.svg)](https://doi.org/10.5281/zenodo.4540326)
 [![license](https://img.shields.io/badge/license-GPLv2-blue.svg)](https://opensource.org/licenses/GPL-2.0)

# rstudio-base

Based on the [Rocker-Project.org](https://rocker-project.org) Docker [RStudio `rstudio` base container](https://hub.docker.com/r/rocker/rstudio) for CyVerse Discovery Environment (DE) data science workbench. CyVerse DE requires additional configuration files (e.g. `nginx`) to be compatible with our Condor and Kubernetes orchestration. 

[An Introduction to Rocker: Docker Containers for R](https://doi.org/10.32614/RJ-2017-065) Carl Boettiger and Dirk Eddelbuettel, The R Journal (2017) 9:2, pages 527-536. [https://doi.org/10.32614/RJ-2017-065 ](https://doi.org/10.32614/RJ-2017-065)

[![CircleCI](https://circleci.com/gh/cyverse-vice/rstudio-base.svg?style=svg)](https://circleci.com/gh/cyverse-vice/rstudio-base)[![DockerHub](https://img.shields.io/badge/DockerHub-gray.svg?style=popout&logo=Docker)](https://hub.docker.com/r/cyversevice/rstudio-base) ![GitHub commits since tagged version](https://img.shields.io/github/commits-since/cyverse-vice/rstudio-base/latest/main?style=flat-square) ![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/cyversevice/rstudio-base)


quick launch | tag | size | metrics | build | 
------------ | --- | ---- | ------- | ------|
<a href="https://de.cyverse.org/de/?type=quick-launch&quick-launch-id=b548d3e2-3310-45ae-8b1f-78e8cce2cfaf&app-id=3548f43a-bed1-11e9-af16-008cfa5ae621" target="_blank"><img src="https://de.cyverse.org/Powered-By-CyVerse-blue.svg"></a> | [![TAG](https://img.shields.io/docker/v/cyversevice/rstudio-base/latest.svg)](https://img.shields.io/docker/v/cyversevice/rstudio-base/latest) | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio-base/latest.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio-base/latest) | [![Docker Pulls](https://img.shields.io/docker/pulls/cyversevice/rstudio-base?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio-base) | [![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/cyversevice/rstudio-base?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio-base)
<a href="https://de.cyverse.org/de/?type=quick-launch&quick-launch-id=97782f8c-8c6f-4969-8c4e-2dd9d5bf5f96&app-id=a8b21a2c-e6f4-11ea-844a-008cfa5ae621" target="_blank"><img src="https://de.cyverse.org/Powered-By-CyVerse-blue.svg"></a> | [![TAG](https://img.shields.io/docker/v/cyversevice/rstudio-base/4.0.0-ubuntu18.04.svg)](https://img.shields.io/docker/v/cyversevice/rstudio-base/4.0.0-ubuntu18.04) | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio-base/4.0.0-ubuntu18.04.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio-base/4.0.0-ubuntu18.04) | [![Docker Pulls](https://img.shields.io/docker/pulls/cyversevice/rstudio-base?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio-base) | [![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/cyversevice/rstudio-base?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio-base)
<a href="https://de.cyverse.org/de/?type=quick-launch&quick-launch-id=97782f8c-8c6f-4969-8c4e-2dd9d5bf5f96&app-id=a8b21a2c-e6f4-11ea-844a-008cfa5ae621" target="_blank"><img src="https://de.cyverse.org/Powered-By-CyVerse-blue.svg"></a> | [![TAG](https://img.shields.io/docker/v/cyversevice/rstudio-base/3.6.3.svg)](https://img.shields.io/docker/v/cyversevice/rstudio-base/3.6.3) | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio-base/3.6.3.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio-base/3.6.3) | [![Docker Pulls](https://img.shields.io/docker/pulls/cyversevice/rstudio-base?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio-base) | [![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/cyversevice/rstudio-base?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio-base)

# Instructions

## Run this Docker locally or on a Virtual Machine

To run these containers, you must first pull them from DockerHub

```
docker pull cyversevice/rstudio-base:latest
```

```
docker run -it --rm -v /$HOME:/app --workdir /app -p 8787:80 -e REDIRECT_URL=http://localhost:8787 cyversevice/rstudio-base:latest
```

The default username is `rstudio` and password is `rstudio1`. To reset the password, add the flag `-e PASSWORD=<yourpassword>` in the `docker run` statement.

## Build your own Docker container and deploy on CyVerse VICE

This container is intended to run on the CyVerse data science workbench, called [VICE](https://cyverse-visual-interactive-computing-environment.readthedocs-hosted.com/en/latest/index.html). 

Unless you plan on making changes to this container, you should just use the existing launch button above. 

###### Developer notes

To build your own container with a Dockerfile and additional dependencies, pull the pre-built image from DockerHub:

```
FROM cyversevice/rstudio-base:latest
```

Follow the instructions in the [VICE manual for integrating your own tools and apps](https://cyverse-visual-interactive-computing-environment.readthedocs-hosted.com/en/latest/developer_guide/building.html).
