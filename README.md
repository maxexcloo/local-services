# Local Services

Separate Docker Compose stacks for services I run locally on macOS with
OrbStack. Each service directory has its own `compose.yaml`. I start and stop them
by hand with Docker Compose and reach the web services through OrbStack's
automatic HTTPS domains.

Start a stack from the repository root, for example:

```sh
docker compose --file onepassword-connect/compose.yaml up --detach
```

[1Password Connect](https://www.1password.dev/connect/get-started)
reads its credentials file from `~/.config/op/connect/` and serves its API at
`https://connect-api.onepassword-connect.orb.local`.

## Development

Install the [shared Mise configuration](https://github.com/maxexcloo/dotfiles#shared-tools--tasks)
before running local Mise tasks.

```sh
mise run check
mise run fmt
```

## Licence

AGPL-3.0 - see [LICENSE](LICENSE).
