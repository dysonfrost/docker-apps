# nginx-rtmp

NGINX + RTMP-Module Image for H.264-Processing (e.g. RTMP, HLS)

* Alipne Linux (3.7)
* FFmpeg 4.0
* NGINX 1.15.0
* [RTMP-Module](https://github.com/sergey-dryabzhinsky/nginx-rtmp-module) Dev-Branche
* Docker-Images for AMD64/X86, ARMHF (e.g. Raspberry-Pi) and AARCH64 (e.g. Pine64)

**Config:**
```sh
$ cat nginx.conf
error_log stderr;
worker_processes auto;

events {
    worker_connections 1024;
}

rtmp {
    allow publish ${PUBLIC_IP};
    deny publish all;
    allow play all;

    server {
        listen 1935;
        chunk_size 8192;
        application live {
	        live on;
	        record off;
	    }
    }
}
```

## Build your own Image

To build a docker image from the `Dockerfile`, run the following command:

```sh
$ docker build -t nginx-rtmp .
```

## Dotenv

Please use the following environment variables:
```sh
$ cat .env
STREAMING_DOMAIN=streaming.example.com
PUBLIC_IP=1.2.3.4
```
## Run your container

To run a container using docker-compose, execute the following command:
```sh
$ docker-compose up -d
```
