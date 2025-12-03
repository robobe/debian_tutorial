
[Post](https://robobe.github.io/new_blog/DevOps/linux/deb_package/shell_script/)

## Install

```bash
sudo apt install fakeroot devscripts debhelper
```

## Check using docker

```bash
docker run -it --rm --name test_deb --hostname test -v `pwd`/debs:/debs ubuntu:22.04 /bin/bash
```



## check service using podman

```
sudo apt install podman
```

```
podman build -f docker/Dockerfile -t ubuntu22:systemd
```

```bash title="run in background"
podman run -it --rm \
  --name systemd_container \
  --privileged \
  --systemd=always \
  --volume /sys/fs/cgroup:/sys/fs/cgroup:ro \
  --volume `pwd`/debs:/debs \
  ubuntu22:systemd \
  /sbin/init
```

```bash title="get prompt"
podman exec -it systemd_container /bin/bash
```