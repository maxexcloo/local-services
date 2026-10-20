# Local Services

Separate Docker Compose stacks for services I run locally on macOS with
OrbStack. Each service directory has its own `compose.yaml`. I start and stop them
by hand with Docker Compose and reach the web services through OrbStack's
automatic HTTPS domains.

Persistent data lives in named volumes, so it survives container replacement.
Keep credentials in your user configuration directory, where each stack expects
them.

Once a stack's credentials are in place, start it from the repository root, for
example:

```sh
docker compose --file onepassword-connect/compose.yaml up --detach
```

[1Password Connect](https://www.1password.dev/connect/get-started)
serves its API at `https://connect-api.onepassword-connect.orb.local`.

## Development

Install the [shared Mise configuration](https://github.com/maxexcloo/dotfiles#shared-tools--tasks)
before running local Mise tasks.

```sh
mise run check
mise run fmt
```

Mise is only needed for development. The checks validate the Compose
configuration, formatting and Renovate configuration without starting any
services. Formatting uses Oxfmt.
