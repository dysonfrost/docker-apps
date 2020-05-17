# Droppy

## Storing data

Two directories will be used, one for configuration and one for the actual files:

- `config`: defaults to `./config`
- `files`: defaults `./files`

droppy maintains an in-memory representation of the files directory. If you're on slow storage and/or serving 100k or more files, the initial indexing on startup will likely take some time.

Create these directories:

```sh
$ mkdir {config,files}
```

## Dotenv

Please use the following environment variables:

```sh
$ cat .env
DROPPY_DOMAIN=droppy.example.com
```

## Run your container

To run a container using docker-compose, execute the following command:

```sh
$ docker-compose up -d
```