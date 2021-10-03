# Vaultwarden

## Storing data

All persistent data is saved under `/data`.
In order to keep them, you have to create the following directory:

```sh
$ mkdir vw-data
```


## Registration of new users

By default, anyone who can access your instance can register for a new account. To disable this, set the `SIGNUPS_ALLOWED` env variable to `false`.

However, the first time you connect, you must set this variable to `true` in the `docker-compose.yml` file:

```yml
environment:
  - SIGNUPS_ALLOWED=true 
```

Create your admin user, then don't forget to reset this variable to `false` and finally restart your container.

*NOTE: You can also configure vaultwarden to send user invitation emails via a SMTP agent, please refer to the [vaultwarden wiki](https://github.com/dani-garcia/vaultwarden/wiki/SMTP-configuration) for more information.*

## Dotenv

Please use the following environment variables:

```sh
$ cat .env
VAULTWARDEN_DOMAIN=vaultwarden.example.com
```

## Run your container

To run a container using docker-compose, execute the following command:

```sh
$ docker-compose up -d
```

## Updating info

Below are the instructions for updating containers via Docker Compose.

- Update all images: `docker-compose pull`
  - or update a single image: `docker-compose pull vaultwarden`

- Let compose update all containers as necessary: `docker-compose up -d`
  - or update a single container: `docker-compose up -d vaultwarden`
- You can also remove the old dangling images: `docker image prune`

Please be careful, as changes in the event of a major version update could break your current configuration.
