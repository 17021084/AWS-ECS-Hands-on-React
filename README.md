# Dockerizing app

url: https://mherman.org/blog/dockerizing-a-react-app/ <br/>

#### Command.

- Build:

```bash
  docker build -t <image>:<version>.
```

- Check Image:

```bash
docker images                                             ✔  10015  13:40:32
REPOSITORY         TAG       IMAGE ID       CREATED              SIZE
ecs-react-sample   dev       03d2f584733d   About a minute ago   512MB
nginxdemos/hello   latest    6746f7a38cc3   3 weeks ago          23.4MB
```

- Run:

```bash
docker run \
    -it \
    --rm \
    -v ${PWD}:/app \
    -v /app/node_modules \
    -p 3001:3000 \
    -e REACT_APP_NAME=trung_abc \
    <image id>
```
