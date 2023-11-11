Configure allowed clients using environment variables:

```
podman run --detach --rm \
  --env RADIUSD_CLIENT_IPADDR=192.168.1.0 \
  --env RADIUSD_CLIENT_NETMASK=24 \
  --env RADIUSD_CLIENT_SECRET=topsecret \
  --volume radiusd:/etc/raddb/certs:ro \
  --publish 192.168.1.1:1812:1812/udp \
  ghcr.io/cynix/radiusd
```

Alternatively, configure allowed clients using file:

```
podman run --detach --rm \
  --volume radiusd:/etc/raddb/certs:ro \
  --volume /path/to/client.conf:/etc/raddb/client.d/client.conf:ro \
  --publish 192.168.1.1:1812:1812/udp \
  ghcr.io/cynix/radiusd
```

where `/path/to/cliente.conf` contains:

```
client_ipaddr = 192.168.1.0
client_netmask = /24
client_secret = topsecret
```
