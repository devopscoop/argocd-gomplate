# AGENTS.md

Instructions for AI coding agents working in this repo.

## Package manifests

This repo ships a `Brewfile` (macOS: `brew bundle`) and a `pkglist.txt` (Arch Linux) that install every local CLI tool the repo uses. Keep them in sync with the code:

- When you add a tool, script, or a new external command that a human runs on their workstation, add the package to BOTH files, with a comment noting what uses it.
- When a tool stops being used, remove it from both files.
- Tools installed by the Dockerfile (gomplate, kubectl, helm, jq, etc.) run inside the image — they do NOT belong in the manifests. Only host-side tools do.
- Verify package names before adding them: `brew info <formula>` for Homebrew, and the official repos/AUR for Arch. If a package is AUR-only, note that in pkglist.txt's header instructions.
- Update the "Prerequisites" section in README.md if the tool list changes.
