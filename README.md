```
podman run --detach --rm \
  --env RADIUSD_CLIENT_IPADDR=192.168.1.0 \
  --env RADIUSD_CLIENT_NETMASK=24 \
  --env RADIUSD_CLIENT_SECRET=topsecret \
  --volume radiusd:/etc/raddb/certs:ro \
  --publish 192.168.1.1:1812:1812/udp \
  ghcr.io/cynix/radiusd
```
