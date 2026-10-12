FROM bitxeno/atvloadly:v0.6.4
# The upstream image leaves /tmp unwritable by apt's unprivileged helper.
RUN chmod 1777 /tmp \
    && apt-get update -o APT::Update::Error-Mode=any \
    && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
        avahi-daemon avahi-utils dbus \
    && rm -rf /var/lib/apt/lists/*
COPY config.yaml /keep/config.yaml
COPY start.sh /usr/local/bin/start-atvloadly
RUN chmod 0755 /usr/local/bin/start-atvloadly
ENTRYPOINT ["/usr/local/bin/start-atvloadly"]
