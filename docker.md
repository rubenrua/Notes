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
