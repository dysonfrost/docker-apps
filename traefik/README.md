# Traefik

## Setup and configure Traefik with Let’s Encrypt

### ACME

You can configure Traefik to use an ACME provider (such as Let's Encrypt) for automatic certificate generation. ACME certificates are stored in a JSON file which must have a 600 file mode.

```sh
$ touch acme.json && sudo chmod 600 acme.json
```

### Basic Auth

To restrict access to Traefik's dashboard, we will use basic auth.

We will first generate a user/password combination for basic authentication using htpasswd . If you don't have it installed, you need to do it first (for example for Ubuntu server) :

```sh
$ sudo apt-get install apache2-utils
```

To generate htpasswd credentials, you can use the following command:

```sh
$ htpasswd -nb <USER> <PASSWORD>
```

The output will be for example (it will be a different result each time you run the above command) :

```sh
<USER>:$apr1$ryHGa8yK$5lRELezhgkUtJxiJ.XTfZ.
```

*NOTE: If you put the `htpasswd` output directly into your `docker-compose.yml` file, instead of using an environment variable (e.g. via the .env file), you must escape the `$`. Then add `| sed -e s/\\$/\$/g` at the end of the htpasswd command string generation.*

### Dotenv

Please use the following environment variables:

```sh
$ cat .env
SECRET=<HTPASSWD-OUTPUT>
EMAIL=email@example.com
DOMAIN=example.com
TRAEFIK_DOMAIN=traefik.example.com
```

### Docker network

Once that’s done you can create the `web` network:

```sh
$ docker network create web
```

## Run your container

To run a container using docker-compose, execute the following command:

```sh
$ docker-compose up -d
```

## Updating info

Below are the instructions for updating containers via Docker Compose.

- Update all images: `docker-compose pull`
  - or update a single image: `docker-compose pull traefik`

- Let compose update all containers as necessary: `docker-compose up -d`
  - or update a single container: `docker-compose up -d 
  traefik`
- You can also remove the old dangling images: `docker image prune`

Please be careful, as changes in the event of a major version update could break your current configuration.
