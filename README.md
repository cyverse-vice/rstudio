[![Project Supported by CyVerse](https://de.cyverse.org/Powered-By-CyVerse-blue.svg)](https://learning.cyverse.org/projects/vice/en/latest/)  [![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4540326.svg)](https://doi.org/10.5281/zenodo.4540326) [![license](https://img.shields.io/badge/license-GPLv2-blue.svg)](https://opensource.org/licenses/GPL-2.0)

# rstudio

Based on the Rocker-Project.org Docker [RStudio base container](https://hub.docker.com/r/rocker/r-base) for CyVerse Discovery Environment (DE) data science workbench. CyVerse DE requires additional configuration files (e.g. `nginx`) to be compatible with Kubernetes orchestration.

[![CircleCI](https://circleci.com/gh/cyverse-vice/rstudio.svg?style=svg)](https://circleci.com/gh/cyverse-vice/rstudio) ![GH actions branch parameter](https://github.com/github/docs/actions/workflows/main.yml/badge.svg?branch=main) ![GitHub commits since tagged version](https://img.shields.io/github/commits-since/cyverse-vice/rstudio/latest/main?style=flat-squa/v/) [![Docker Pulls](https://img.shields.io/docker/pulls/cyversevice/rstudio?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio) 

quick launch | size | 
------------ | ---- | 
<a href="https://de.cyverse.org/apps/de/3548f43a-bed1-11e9-af16-008cfa5ae621/launch?quick-launch-id=81b187d6-cc94-4c53-81b5-f09f31c9c8ba" target="_blank"><img src="https://img.shields.io/badge/Rstudio-latest-blue?style=plastic&logo=rstudio"></a> | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio/latest.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio/latest)
<a href="https://de.cyverse.org/apps/de/15c46f9e-bb1a-11eb-97db-008cfa5ae621/launch?quick-launch-id=758ace16-7629-4d11-a78d-a77666832c1d" target="_blank"><img src="https://img.shields.io/badge/Rstudio-4.0.5-blue?style=plastic&logo=rstudio"></a> | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio/4.0.5.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio/4.0.5)
<a href="https://de.cyverse.org/apps/de/01d05704-a784-11eb-98a3-008cfa5ae621/launch?quick-launch-id=5a1cc90c-9139-4c9f-838f-0c101392d1cf" target="_blank"><img src="https://img.shields.io/badge/Rstudio-4.0.0ubuntu18.04-blue?style=plastic&logo=rstudio"></a> | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio/4.0.0-ubuntu18.04.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio-verse/4.0.0-ubuntu18.04) | [![Docker Pulls](https://img.shields.io/docker/pulls/cyversevice/rstudio?color=blue&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/rstudio)
<a href="https://de.cyverse.org/apps/de/a8b21a2c-e6f4-11ea-844a-008cfa5ae621/launch?quick-launch-id=dc645017-b1a8-451e-a99c-9030a4bc24e1" target="_blank"><img src="https://img.shields.io/badge/Rstudio-3.6.3-blue?style=plastic&logo=rstudio"></a> | [![SIZE](https://img.shields.io/docker/image-size/cyversevice/rstudio/3.6.3.svg)](https://img.shields.io/docker/image-size/cyversevice/rstudio/3.6.3) 

# Instructions

## Run this Docker locally or on a Virtual Machine

To run these containers, you must first pull them from DockerHub

```
docker pull cyversevice/rstudio:latest
```

```
docker run -it --rm -v /$HOME:/app --workdir /app -p 8787:80 -e REDIRECT_URL=http://localhost:8787 cyversevice/rstudio:latest

or

docker run -it --rm -p 8787:80 -e REDIRECT_URL=http://localhost:8787 harbor.cyverse.org/vice/rstudio/rstudio:latest
```

The default username is `rstudio` and password is `rstudio1`. To reset the password, add the flag `-e PASSWORD=<yourpassword>` in the `docker run` statement.

## Build your own Docker container and deploy on CyVerse VICE

This container is intended to run on the CyVerse data science workbench, called [VICE]([https://cyverse-visual-interactive-computing-environment.readthedocs-hosted.com/en/latest/index.html](https://learning.cyverse.org/de/using_apps/#advanced-features-in-the-discovery-environment)). 

###### Developer notes

To build your own container with a Dockerfile and additional dependencies, pull the pre-built image from DockerHub:

```
FROM harbor.cyverse.org/vice/rstudio/rstudio:latest
```

Follow the instructions on how to [Integrate your own Containers and Apps into CyVerse](https://learning.cyverse.org/de/create_apps/)
