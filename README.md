
## Install

```bash
sudo apt install fakeroot devscripts debhelper
```

## Check using docker

```bash
docker run -it --rm --name test_deb --hostname test -v `pwd`/debs:/debs ubuntu:22.04 /bin/bash
```

## Tutorial: Add postinst and postrm script file


## Tutorial: Add systemd service

[!NOTE]
check compat is newer capability version: 13

Modern dh automatically runs `dh_installsystemd` based on the presence of `debian/myapp.service`


```bash title="journalctl"
journalctl -u my-tools.service
#
Dec 01 08:21:48 omen systemd[1]: Started my-tools.service - mytool background service.
Dec 01 08:21:48 omen my-tool.sh[627996]: hello my-tool
Dec 01 08:21:48 omen systemd[1]: my-tools.service: Deactivated successfully.
```

```bash title="systemctl status"
systemctl status my-tools.service
○ my-tools.service - mytool background service
     Loaded: loaded (/usr/lib/systemd/system/my-tools.service; enabled; preset: enabled)
     Active: inactive (dead) since Mon 2025-12-01 08:21:48 IST; 1min 9s ago
   Duration: 2ms
    Process: 627996 ExecStart=my-tool.sh (code=exited, status=0/SUCCESS)
   Main PID: 627996 (code=exited, status=0/SUCCESS)
        CPU: 1ms

Dec 01 08:21:48 omen systemd[1]: Started my-tools.service - mytool background service.
Dec 01 08:21:48 omen my-tool.sh[627996]: hello my-tool
Dec 01 08:21:48 omen systemd[1]: my-tools.service: Deactivated successfully.
```

### multiple service