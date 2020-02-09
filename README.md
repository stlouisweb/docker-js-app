# Dockerized JavaScript Web App

This app is a reference architecture for Isomporhic JavaScript applications, the front end is a static SPA style app with its own NodeJS server for SSR and optimized code-splitting, the backend is NodeJS offering a REST API and real-time websocket connections.

- frontend: NextJS (connects to backend with websocket client)
- backend: FeathersJS
- database: MongoDB 
- file-system: Minio (S3 compatibile object store
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