
[Post](https://robobe.github.io/new_blog/DevOps/linux/deb_package/shell_script/)

## Install

```bash
sudo apt install fakeroot devscripts debhelper
```

## Check using docker

```bash
docker run -it --rm --name test_deb --hostname test -v `pwd`/debs:/debs ubuntu:22.04 /bin/bash
```


