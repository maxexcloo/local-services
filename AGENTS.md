# AGENTS.md

## Project Overview

This repository owns independent Docker Compose services run locally through
OrbStack on macOS.

## Conventions

- Bind published service ports to localhost. Keep host networking limited to
  services that require LAN discovery, with their UI bound to localhost.
- Keep credentials out of Git and mount credential files read-only.
- Keep each service in its own directory with a `compose.yaml` file.
- Keep executable startup code in its own source file.
- Keep persistent application data in named volumes. Preserve existing volumes
  and pairing records when replacing containers.
- Keep service startup and shutdown manual; validate configuration locally.
- Pin upstream images to stable releases. Build local images through Compose.

## Verification

Run `mise run check` after changes. For Dockerfile or startup changes, build the
changed service and verify its health and retained data locally. Connect runtime
checks require a supplied credentials file; configuration checks do not.
