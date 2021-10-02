# Duplicati

## Storing data

Two directories will be used, one for configuration and one for the source files to backup:

- `config`: defaults to `./config`
- `source`: defaults to the root directory of this repository

Create the config directory:

```sh
$ mkdir config
```

## User / Group Identifiers

When using volumes (-v flags) permissions issues can arise between the host OS and the container, to avoid this issue you must specify the user PUID and group PGID.

Ensure any volume directories on the host are owned by the same user you specify and any permissions issues will vanish like magic.

Find your PUID and PGID:

```sh
$ id
uid=1000(dockeruser) gid=1000(dockergroup) groups=1000(dockergroup)
```

## Dotenv

Please use the following environment variables:

```sh
$ cat .env
DUPLICATI_DOMAIN=duplicati.example.com
PUID=<USER_UID>
PGID=<USER_GID>
TZ=Europe/Paris
```

## Run your container

To run a container using docker-compose, execute the following command:

```sh
$ docker-compose up -d
```

## Updating info

Below are the instructions for updating containers via Docker Compose.

- Update all images: `docker-compose pull`
  - or update a single image: `docker-compose pull duplicati`

- Let compose update all containers as necessary: `docker-compose up -d`
  - or update a single container: `docker-compose up -d duplicati`
- You can also remove the old dangling images: `docker image prune`

Please be careful, as changes in the event of a major version update could break your current configuration.
