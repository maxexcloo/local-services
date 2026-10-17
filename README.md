# Local Services

Independent Docker Compose stacks for local services on macOS with OrbStack.
Each service directory contains its own `compose.yaml`. Start and stop services
manually through OrbStack; access web services using its automatic HTTPS domains.

Persistent data lives in named volumes and survives container replacement. Keep
credentials in your user configuration directory, as referenced by each stack.

After supplying the credentials required by a stack, start it from the repository
root, for example:

```sh
docker compose --file onepassword-connect/compose.yaml up --detach
```

## Development

Install the [shared Mise configuration](https://github.com/maxexcloo/dotfiles#shared-tools--tasks)
before running local Mise tasks.

```sh
mise install
mise run check
mise run fmt
```

Mise is only needed for development. Checks validate Compose configuration,
formatting and Updatecli manifests without starting services. Formatting uses
Oxfmt.

Preview dependency updates with `mise run dependencies:check`; apply reviewed changes with
`mise run dependencies:update`. Updatecli uses native Docker Compose discovery with the `docker` update group.
