# Caddy with labels


This caddy reverse proxy doesn't need a configuration file, it uses Docker container labels to
determine what to proxy, and on what hostname (defaults to container name), domain (defaults to `loc.alho.st`)
or path (defaults to `/`).

> *NOTE:* any container you want caddy_proxy to reverse proxy must also be connected to the `caddy_proxy` network: `--network caddy_proxy`

To customise how it proxies, you can use the following labels on your container:

* `virtual.port` - the port that the service is listening on inside the container
* `virtual.host` - the hostname to be prefixed on the `domain`
* `virtual.domain` - the domain suffix
* `virtual.path` - the path prefix - note that this matches any path that starts with this prefix.


## Future ideas

I'd love to add a small service that can take any incoming container `run` command that is http based (compose, swarm, whatever), and converts it to use domain based reverse proxying.

Figure out how to add the libdns and dns based lets encrypt support back in - without the user needing to build a new caddy container, and with some simplified way to configure the user authentication to the DNS api.

Authentication - again, without requiring too much

magic dashboard of hooked up backends...
