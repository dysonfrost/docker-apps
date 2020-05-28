# Calibre

## Storing data

Two directories will be used, one for configuration and one for calibre library:

- `config`: defaults to `./config`
- `books`: defaults `./books`


## User / Group Identifiers

When using volumes, permissions issues can arise between the host OS and the container.

Ensure any volume directories on the host are owned by the same user you specify and any permissions issues will vanish like magic.

The first time you run a calibre container, Docker will create these volumes. Pay attention to the `config` directory and set the same owner for the `books` directory using the following command:

```sh
$ sudo chown <uid>:<gid> books
```

## Calibre database

Calibre requires you to have an existing calibre database at the `/books` location.

Download a freshly generated `metadata.db` file [here](https://drive.google.com/file/d/1nd00hG0CIB7jw2sr9L6V1TK5gIDe3vbq/view?usp=sharing).  
Then place it into the `./books` directory.


## Dotenv

Please use the following environment variables:

```sh
$ cat .env
CALIBRE_DOMAIN=calibre.example.com
```

## Run your container

To run a container using docker-compose, execute the following command:

```sh
$ docker-compose up -d
```

## Application Setup

Webui can be found at https://calibre.example.com

On the initial setup screen, enter /books as your calibre library location.

**Default admin login**: 
- *Username*: admin
- *Password*: admin123

Unrar is included by default and needs to be set in the Calibre-Web admin page (Basic Configuration:External Binaries) with a path of `/usr/bin/unrar`

**x86-64 only** Calibre has the optional ability to enable ebook conversion. To use this option set the converter tool path to `/usr/bin/ebook-convert` in the Calibre-Web admin page (Basic Configuration:External Binaries).

## Updating info

Below are the instructions for updating containers via Docker Compose.

- Update all images: `docker-compose pull`
  - or update a single image: `docker-compose pull calibre-web`

- Let compose update all containers as necessary: `docker-compose up -d`
  - or update a single container: `docker-compose up -d 
  calibre-web`
- You can also remove the old dangling images: `docker image prune`

Please be careful, as changes in the event of a major version update could break your current configuration.
