
# from https://hub.docker.com/_/caddy
# 
# should really version things, but i don't want to...

FROM caddy:builder AS builder

RUN xcaddy build \
    --with github.com/lucaslorentz/caddy-docker-proxy/plugin/v2=github.com/onaci/caddy-docker-proxy/plugin/v2@templates

FROM caddy:latest

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
COPY Caddyfile /
ENV CADDY_DOCKER_CADDYFILE_PATH=/Caddyfile

COPY templates/* /config/caddy/docker-proxy/

CMD [ "caddy", "docker-proxy" ]