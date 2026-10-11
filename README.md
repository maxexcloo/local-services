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

## Atvloadly

```sh
docker volume create atvloadly-data
docker compose --file atvloadly/compose.yaml up --build --detach
```

Open [Atvloadly](http://localhost:5533). The external `atvloadly-data` volume holds
configuration, pairing records, signing keys and application data. It preserves
the existing installation and is retained when the Compose stack is removed.

The image includes Avahi and D-Bus for Apple TV discovery. Host networking is
required for discovery in OrbStack. The default configuration binds the UI to
localhost; existing volume configuration takes precedence. Automatic refreshes
require the Mac to be awake, OrbStack to be running and the Apple TV to be reachable.

## Development

```sh
mise run setup
mise run check
```

Checks validate both Compose stacks, formatting, workflow syntax and the startup
script. They do not start services or require Connect credentials. Renovate
proposes dependency updates for manual review.

## Status & Shutdown

```sh
docker compose --file atvloadly/compose.yaml ps
docker compose --file onepassword-connect/compose.yaml ps
docker compose --file atvloadly/compose.yaml down
docker compose --file onepassword-connect/compose.yaml down
```

These shutdown commands retain data volumes.
