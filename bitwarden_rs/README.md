# Bitwarden

## Storing data

All persistent data is saved under `/data`.
In order to keep them, you have to create the following directory:

```sh
$ mkdir bw-data
```


## Registration of new users

By default, anyone who can access your instance can register for a new account. To disable this, set the `SIGNUPS_ALLOWED` env variable to `false`.

However, the first time you connect, you must set this variable to `true` in the `docker-compose.yml` file:

```yml
environment:
  - SIGNUPS_ALLOWED=true 
```

Create your admin user, then don't forget to reset this variable to `false` and finally restart your container.

*NOTE: You can also configure bitwarden_rs to send user invitation emails via a SMTP agent, please refer to the [bitwarden_rs wiki](https://github.com/dani-garcia/bitwarden_rs/wiki/SMTP-configuration) for more information.*

## Dotenv

Please use the following environment variables:

```sh
$ cat .env
BITWARDEN_DOMAIN=bitwarden.example.com
```

## Run your container

To run a container using docker-compose, execute the following command:

```sh
$ docker-compose up -d
```