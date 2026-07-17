# Brewfile for argocd-gomplate
#
# Installs every CLI tool used or referenced by this repo.
# Usage: brew bundle
#
# Note: the tools inside the image (gomplate, kubectl, helm, jq, etc.) are
# installed by the Dockerfile and run in the cluster — they are NOT local
# dependencies. Building the image only needs Docker.

# Docker Desktop - `docker build` / `docker buildx build` for the image.
# Includes buildx for the documented multi-platform build.
# (Alternative: `brew install docker docker-buildx colima` for a desktop-free setup.)
cask "docker-desktop"

# git - cloning and contributing
brew "git"
