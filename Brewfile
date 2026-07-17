# Brewfile for argocd-gomplate
#
# Installs every CLI tool used or referenced by this repo.
# Usage: brew bundle
#
# Note: the tools inside the image (gomplate, kubectl, helm, jq, etc.) are
# installed by the Dockerfile and run in the cluster — they are NOT local
# dependencies. Building the image only needs Docker.

# colima + Docker CLI - `docker build` / `docker buildx build` for the image.
# colima provides the Docker engine in a lightweight VM; run `colima start`
# before building. (Alternative: the docker-desktop cask.)
brew "colima"
brew "docker"

# docker-buildx - the documented multi-platform build (`docker buildx build`).
# Homebrew installs it standalone; see `brew info docker-buildx` caveats for
# registering it as a Docker CLI plugin.
brew "docker-buildx"

# git - cloning and contributing
brew "git"
