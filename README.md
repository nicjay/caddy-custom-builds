# Caddy Docker Custom Build

Adds support for:  
https://github.com/caddy-dns/cloudflare  
https://github.com/hslatman/caddy-crowdsec-bouncer

```dockerfile
FROM caddy:2.7.6-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/cloudflare \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http

FROM caddy:2.7.6

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
```
