# DOCKER

> Use podman, it is daemonless

## Tips:

### execute other platform images

```
sudo apt-get update
sudo apt-get install qemu-user-static binfmt-support
sudo update-binfmts --enable qemu-arm64

# sudo pacman -S qemu-user-static
# sudo pacman -S qemu-user-static-binfmt
docker run -it --platform linux/arm64 --rm   ubuntu:noble bash
```

### x11/wayland access

```
docker run -ti -u $(id -u):$(id -g) -v /etc/passwd:/etc/passwd:ro -v /etc/group:/etc/group:ro -e XDG_RUNTIME_DIR -v /run/user/1000:/run/user/1000 -v /tmp/.X11-unix/X0:/tmp/.X11-unix/X0 -e DISPLAY  -v `realpath ws`:/ws  archlinux bash
```

TODO: XAUTHORITY, sudo
