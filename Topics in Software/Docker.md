# Important concepts:
- Docker images: the blueprint of your system, includes the OS, necessary packages, and configurations. **Remote registry** enable cross device usage.
- Docker volume: the work folder that contain your codes and libraries. This can be mounted to continue work on different devices.

# Dockerfile vs Docker Image:
- Docker image: Fast build time for complex images and consistent to avoid packages mismatch
- Dockerfile: use for simples images with 2-3 minutes of build time and require reproducibility from source 

# Setting up Docker:
- Add:  echo "xhost +local:" >> ~/.bashrc
- Login: 
```docker login ghcr.io -u baodn19 -p <token_key>```
- Pull image: `docker pull ghcr.io/baodn19/go2:latest`
- Run image: `docker run -it --name go2_container --network host --privileged -e DISPLAY=$DISPLAY -v $(pwd):/home/ubuntu/go2_ws/src/go2 ghcr.io/baodn19/go2:latest`
- Re-enter the container: `docker start -ai <container_name>`

# Cross-platform (AMD64 and ARM64) build:
1. Create and Configure Buildx Builder
``` bash
# Install QEMU for cross-platform emulation
docker run --rm --privileged tonistiigi/binfmt --install all

# Create a new builder instance
docker buildx create --name multiarch-builder --use

# Bootstrap the builder
docker buildx inspect --bootstrap
```
2. Build and Push Multi-Arch Image
``` bash

```

# Error & Fix:
| Error                                                                                                                      | Fix                                                      |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Colcon building inside dockerfile and encounter:<br>`'builtin_interfaces__rosidl_generator_c' which couldn't be found<br>` | Remove the colcon build and do it later in the container |
| Building dockerfile and encounter:<br>`no space left on device`                                                            | Free up space with `jlumbroso/free-disk-space@main`      |
|                                                                                                                            |                                                          |
