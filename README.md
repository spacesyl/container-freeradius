Configure allowed clients using environment variables:

```
podman run --detach --rm \
  --env RADIUSD_CLIENT_IPADDR=192.168.1.0/24 \
  --env RADIUSD_CLIENT_SECRET=topsecret \
  --volume radiusd:/etc/raddb/certs:ro \
  --publish 192.168.1.1:1812:1812/udp \
  ghcr.io/spacesyl/freeradius
```

Alternatively, configure allowed clients using file:

```
podman run --detach --rm \
  --volume radiusd:/etc/raddb/certs:ro \
  --volume /path/to/client.conf:/etc/raddb/client.d/client.conf:ro \
  --publish 192.168.1.1:1812:1812/udp \
  ghcr.io/spacesyl/freeradius
```

where `/path/to/client.conf` contains:

```
client_ipaddr = 192.168.1.0/24
client_secret = 'topsecret'
```
