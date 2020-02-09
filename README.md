# Dockerized JavaScript Web App

This app is a reference architecture for Isomporhic JavaScript applications, the front end is a static SPA style app with its own NodeJS server for SSR and optimized code-splitting, the backend is NodeJS offering a REST API and real-time websocket connections.

- frontend: NextJS (connects to backend with websocket client WIP)
- backend: FeathersJS WIP
- database: MongoDB 
- file-system: Minio (S3 compatibile object store)
- web-server-proxy: Nginx with SSL termination


### Build the backend container

To update the backend FeathersJS app use the `docker build` command

```
$ cd ./backend
$ docker build -t backend .
```

### Build the frontend container

To update the frontend FeathersJS app use the `docker build` command

```
$ cd ./frontend
$ docker build -t frontend .
```

### Start the app

```
$ docker-compose up -d
```

### Local DNS set up

To use the local domains modify your hosts file

`sudo vi /etc/host` and add this

```
127.0.0.1   local.app
127.0.0.1   storage.local.app
127.0.0.1   api.local.app
```

use [mkcert](https://github.com/FiloSottile/mkcert) to install the ssl certs in your local trust authority

```
$ cd ./volumes/nginx/private
$ export CAROOT=${PWD}
$ mkcert -install
$ docker exec -it reverse_proxy nginx -s reload
```