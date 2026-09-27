# Docker Image

A Docker image is a **read-only package** containing everything needed to create a container.

---

## Image Layers

A Docker image is usually made of **multiple layers**.

They can contain:

- Base OS files
- Runtime
- Dependencies
- Your application

Docker can reuse layers instead of downloading/building everything again.

That's why layers are important for **speed and storage efficiency**.

---

## Why Layers Matter

Suppose you have two applications:

- **App A** using Node.js + Express
- **App B** using Node.js + React server

Both applications can use the same Node.js base image, so Docker can reuse the common layers instead of storing the same Node.js files separately for each application.

This saves **storage space**, speeds up **image building**, and makes Docker more efficient.

---

## Image Tags

A tag is a **human-readable label/version** for an image.

---

## Image ID

It identifies the particular image stored locally.

---

## Image Repository

A repository is where images with related names/tags are organized.

---

## Base Images

A **base image** is the starting point for building another image.

Common base images:

- `ubuntu`
- `alpine`
- `node`
- `python`
- `nginx`

---

## Image Caching

Docker reuses previously built layers whenever possible.

During the first build, Docker builds each layer one by one.

If you later change only your source code, Docker can reuse the unchanged layers and rebuild only the layer affected by the change.

This avoids rebuilding everything from scratch and makes subsequent image builds much faster.

---

## Image Immutability

Docker images are treated as **immutable**, meaning an existing image is not modified after it is created.

If you need to make changes, you update the source or Dockerfile and build a **new image** containing those changes.

This makes deployments more predictable and makes it easier to roll back to a previous image when needed.

---

# Image Naming

A Docker image can be represented like:

```text
registry/username/repository:tag
```

---

# Useful Commands

```powershell
# check all images present locally
docker images
docker image ls

# download an image
docker pull image_name

# inspect an image (here mentioned nginx)
# gives detailed information about the image - Image ID, Architecture, OS, Created time, Layers
# Environment, Configuration, Entrypoint, Command
docker image inspect nginx

# image build history
docker image history nginx

# removes the local image
# If a container is using that image, Docker may not allow you to remove it normally.
# Remove the container first and later remove the image.
docker image rm nginx
```

---

# Image vs Container

| Image                                | Container                             |
| ------------------------------------ | ------------------------------------- |
| Read-only                            | Has a writable container layer        |
| Blueprint/template                   | Running instance                      |
| Used to create containers            | Created from an image                 |
| Stored locally or in a registry      | Runs on the Docker Engine             |
| Does not run by itself               | Can be started, stopped, and deleted  |
| One image can create many containers | Each container is a separate instance |
