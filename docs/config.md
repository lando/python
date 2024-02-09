---
title: Configuration
description: Learn how to configure the Lando Python service.
---

# Configuration

Here are the configuration options, set to the default values, for this service. If you are unsure about where this goes or what this means, we *highly recommend* scanning the [services documentation](https://docs.lando.dev/core/v3/lando-service.html) to get a good handle on how the magicks work.

Also note that options, in addition to the [build steps](https://docs.lando.dev/core/v3/lando-service.html#build-steps) and [overrides](https://docs.lando.dev/core/v3/lando-service.html#overrides) that are available to every service, are shown below:

```yaml
services:
  myservice:
    type: python:3.7
    port: 80
    ssl: false
    command: tail -f /dev/null
```

## Specifying a command

Note that if you *do not* define a `command` for this service, it will effectively be a "cli" container (e.g. it will not serve or run an application by default but will be available to run `python` commands against).

If you want to actually launch a `python` application, consider setting the `command` to something as shown below:

```yaml
services:
  myservice:
    type: python
    command: /app/my-server.py
```

## Setting a port

While we assume your `python` service is running on port `80`, we recognize that many `python` app's also run on port `8000` or otherwise. You can easily change our default to match whatever your app needs.

```yaml
services:
  myservice:
    type: python
    port: 8000
```

## Using SSL

Also note that `ssl: true` will only generate certs in the [default locations](https://docs.lando.dev/core/v3/security.html). It is up to the user to use the certs and secure port correctly in their application like as in the `python` snippet below:

```yaml
services:
  myservice:
    type: python
    ssl: true
    port: 443
```

```python
// Starting HTTPS server
httpsd = HTTPServer(('0.0.0.0', 443), myHandler)
httpsd.socket = ssl.wrap_socket (httpsd.socket, server_side=True, certfile='/certs/cert.crt', keyfile='/certs/cert.key')
print('starting https server...')
httpsd.serve_forever()
```

## Adding tooling commands

By default a service will not do any tooling routing for you but you can add helpful `lando` commands.

```yaml
tooling:
  dotnet:
    service: myservice
```

You can then invoke them on the command line.

```bash
lando dotnet
```

Lando tooling is actually pretty powerful so definitely check out [the rest](https://docs.lando.dev/core/v3/tooling.html) of its cool features.

## Adding routing

By default a service will not do any proxy routing for you but you can add your own.

```yaml
proxy:
  myservice:
    - myapp.lndo.site
    - something.else.local
```

Lando proxying is actually pretty powerful so definitely check out [the rest](https://docs.lando.dev/core/v3/proxy.html) of its cool features.
