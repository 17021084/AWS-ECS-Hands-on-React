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

# Push Build Image in Register

1. Docker hub.

Prerequired: signed in hub.docker.com <br/>

- Create new public repository
- Rename images.

```bash
docker tag <existing-image> <hub-user>/<repo-name>[:<tag>]
```

- push to docker hub repo

```bash
docker commit <existing-container> <hub-user>/<repo-name>[:<tag>]
```

2. ECR

**Images Size < 0.5gb free**

- Step:1 Tạo repo
- Step:2 Xem view command :v
- Step:3 login

```bash
# public repo. private se khac
aws ecr-public get-login-password --region <region> | docker login --username AWS --password-stdin public.ecr.aws/e4y8g9s1
```

- build (optional)
- tag

```bash
docker tag  <image>:<version> public.ecr.aws/e4y8g9s1/demo-nginx:latest
```

- push

```bash
docker push public.ecr.aws/e4y8g9s1/demo-nginx:latest
```
