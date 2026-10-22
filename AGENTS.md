# AGENTS.md

## Project Overview

This repository owns independent Docker Compose services run locally through
OrbStack on macOS.

## Conventions

- Keep each service in its own directory with a `compose.yaml` file.
- Keep persistent application data in named volumes. Preserve existing volumes
  and pairing records when replacing containers.
- Start and stop services manually; add no startup automation beyond
  `restart: unless-stopped`.
- Prefer OrbStack's automatic domains and HTTPS without published host ports.
  Bind required published ports to localhost. Use host networking only for LAN
  discovery, with service UIs bound to localhost.
- Store credentials under `${XDG_CONFIG_HOME:-$HOME/.config}`, outside the
  repository, and mount credential files read-only.
- The Connect endpoint is its OrbStack domain. Homelab consumes it through
  `op://Homelab/OpenTofu/op_connect_host`; update that consumer when changing
  the endpoint.

## Verification

Run `mise run check` after changes. For image, mount, networking or startup
changes, verify the affected service's health, access and retained data locally.
Connect runtime checks require a supplied credentials file; configuration checks
do not.
