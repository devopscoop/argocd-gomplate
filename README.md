# ArgoCD Gomplate Image

Container image that provides the tooling needed for ArgoCD's gomplate-based config management plugin. This image is used as a sidecar container in ArgoCD's repo-server to process Helm charts with gomplate templating.

## Overview

This repository contains the Dockerfile for building a container image with Helm, gomplate, and kubectl. The image is used by the ArgoCD plugin configuration defined in the [argocd-config](https://github.com/arturo-builds-infra/argocd-config) repository.

**Part of the ArgoCD ApplicationSet Pattern:**
- Main pattern repository: [argocd-applicationset-pattern](https://github.com/arturo-builds-infra/argocd-applicationset-pattern)
- ArgoCD plugin configuration: [argocd-config](https://github.com/arturo-builds-infra/argocd-config)
- **This repository**: Container image with required tooling

## What's in the Image

The image is based on Alpine Linux and includes:

- **kubectl** - Latest stable Kubernetes CLI
- **helm** - Latest stable Helm CLI  
- **gomplate** - v3.11.7 templating engine
- **bash**, **curl**, **jq**, **gettext** - Supporting utilities

## Container Image

**Public image:** `ghcr.io/arturo-builds-infra/argocd-gomplate:latest`

The image is automatically built and published to GitHub Container Registry on every push to the main branch.

## Usage

This image is used as a sidecar container in ArgoCD's repo-server deployment. The actual plugin configuration (the script that uses these tools) is defined in the [argocd-config](https://github.com/arturo-builds-infra/argocd-config) repository.

For complete setup instructions and plugin configuration, see [argocd-config](https://github.com/arturo-builds-infra/argocd-config).

For the application pattern that uses this plugin, see [argocd-applicationset-pattern](https://github.com/arturo-builds-infra/argocd-applicationset-pattern).

## Prerequisites

Building the image locally only requires Docker (with buildx for multi-platform builds) — everything else ships inside the image. Package manifests are included:

- macOS, using [Homebrew](https://brew.sh/) and the `Brewfile`:

  ```shell
  brew bundle
  ```

- Arch Linux, using the `pkglist.txt` (all packages are in the official repos):

  ```shell
  grep -vE '^(#|$)' pkglist.txt | sudo pacman -S --needed -
  ```

On other operating systems, install Docker manually.

## Building the Image

```bash
docker build -t argocd-gomplate:latest .
```

For multi-platform builds:

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t argocd-gomplate:latest .
```

## License

Apache 2.0
