# Local Services

Independent Docker Compose stacks for local services on macOS with OrbStack.
Each service directory contains its own `compose.yaml`. Start and stop services
manually through OrbStack; access web services using its automatic HTTPS domains.

Persistent data lives in named volumes and survives container replacement. Keep
credentials in your user configuration directory, as referenced by each stack.

## Development

```sh
mise install
mise run check
mise run fmt
```

Mise is only needed for development. Checks validate Compose configuration,
formatting and Updatecli manifests without starting services. Formatting uses
Prettier.

Preview dependency updates with `mise run updates`; apply reviewed changes with
`mise run updates apply`. Updatecli uses native Docker Compose discovery and
checks project-specific Mise tools. Update groups follow their ecosystems:
`docker` and `mise`.
