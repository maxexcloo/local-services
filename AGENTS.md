# AGENTS.md

## Project Overview

This repository owns independent Docker Compose services run locally through
OrbStack on macOS.

## Conventions

- Keep dependency updates manual through native Updatecli discovery. Name
  policies and groups by the tool or ecosystem they manage.
- Keep each service in its own directory with a `compose.yaml` file.
- Keep executable startup code in its own source file.
- Keep persistent application data in named volumes. Preserve existing volumes
  and pairing records when replacing containers.
- Keep README content general and brief; keep service settings in Compose.
- Keep service startup and shutdown manual; validate configuration locally.
- Pin upstream images to stable releases. Build local images through Compose.
- Prefer OrbStack's automatic domains and HTTPS without published host ports.
  Bind required published ports to localhost. Use host networking only for LAN
  discovery, with service UIs bound to localhost.
- Store credentials under `${XDG_CONFIG_HOME:-$HOME/.config}`, outside the
  repository, and mount credential files read-only.

## Verification

Run `mise run check` after changes. For Dockerfile, image, mount, networking or
startup changes, verify the affected service's health, access and retained data
locally. Build changed local images through Compose before runtime checks;
services using upstream images do not need a build. Connect runtime checks require
a supplied credentials file; configuration checks do not.
