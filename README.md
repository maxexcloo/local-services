# Local Services

Independent Docker Compose stacks for local services on macOS with OrbStack.
Run commands from this directory.

## 1Password Connect

Save your Connect server credentials as
`onepassword-connect/1password-credentials.json`, then start the stack:

```sh
docker compose --file onepassword-connect/compose.yaml up --detach
```

The credentials file is mounted read-only and excluded from Git. Both containers
share the named `onepassword-connect_data` volume. The API is available at
`http://localhost:8080`; clients supply their own Connect access token. The sync
service has no published port. Follow the
[1Password setup instructions](https://www.1password.dev/connect/get-started) to
obtain credentials and client tokens.

## Development

```sh
mise run setup
mise run check
```

Checks validate the Compose stack, formatting and workflow syntax. They do not
start services or require Connect credentials. Updatecli previews local dependency updates
for manual review.

## Status & Shutdown

```sh
docker compose --file onepassword-connect/compose.yaml ps
docker compose --file onepassword-connect/compose.yaml down
```

These shutdown commands retain data volumes.
