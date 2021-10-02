# Self-Hosted Docker containers

This repository lists Docker containers I’ve created to run some popular applications.  Most of the applications implemented have a graphical user interface (GUI). They can be accessed through a modern web browser.

## Applications

- [bitwarden_rs](https://github.com/dani-garcia/bitwarden_rs) - A lightweight version written in rust of bitwarden, a password manager with webapp, browser extension, and mobile app.
- [calibre-web](https://github.com/linuxserver/docker-calibre-web) - Calibre-web is a web app providing a clean interface for browsing, reading and downloading eBooks using an existing Calibre database.
- [droppy](https://github.com/silverwind/droppy) - Droppy is a self-hosted cloud server with an interface similar to desktop file managers and has capabilities to edit files on-the-fly as well as view and playback media directly in the browser.
- [duplicati](https://github.com/duplicati/duplicati) - Duplicati is a free, open source, backup client that securely stores encrypted incremental, compressed backups on cloud storage services and remote file servers.
- [nginx-rtmp](https://github.com/tiangolo/nginx-rtmp-docker) - NGINX server with nginx-rtmp-module for multimedia / video streaming, built from Nginx 1.15.0 and nginx-rtmp-module 1.2.1. The main purpose is to allow streaming from OBS Studio to different clients at the same time.
- [traefik](https://traefik.io/) - Træfɪk is a modern HTTP reverse proxy and load balancer made to deploy microservices with ease. It supports several backends (Docker, Swarm, Kubernetes, Etcd, Rancher, …) to manage its configuration automatically and dynamically.

## Prerequisites

- Docker
- Docker Compose
- A domain

## Load environment variables

Create a `.env` file in the root directory of any application. Add environment-specific variables on new lines in the form of NAME=VALUE. For example:

```sh
$ cat app/.env
DB_HOST=localhost
DB_USER=root
DB_PASS=s1mpl3
```

## Run an application

Because each application depends on its own configuration, you will find a detailed README in each subdirectory.
