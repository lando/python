---
title: Python Lando Plugin
description: Add a highly configurable Python service to Lando for local development with all the power of Docker and Docker Compose.
next: ./config.html
---

# Python

[Python](https://www.python.org/) is a programming language that lets you work more quickly and integrate your systems more effectively.

You can easily add it to your Lando app by adding an entry to the [services](https://docs.lando.dev/core/v3/lando-service.html) top-level config in your [Landofile](https://docs.lando.dev/core/v3).


```yaml
services:
  myservice:
    type: python
```

## Supported versions

*   [3](https://hub.docker.com/_/python)
*   [3.12](https://hub.docker.com/_/python)
*   [3.11](https://hub.docker.com/_/python)
*   [3.10](https://hub.docker.com/_/python)
*   [3.9](https://hub.docker.com/_/python)
*   [3.8](https://hub.docker.com/_/python)
*   **[3.7](https://hub.docker.com/_/python)** **(default)**
*   [3.6](https://hub.docker.com/_/python)
*   [3.5](https://hub.docker.com/_/python)
*   [custom](https://docs.lando.dev/core/v3/lando-service.html#overrides)

## Legacy versions

You can still run these versions with Lando but for all intents and purposes they should be considered deprecated (e.g. YMMV and do not expect a ton of support if you have an issue).

*   [2.7](https://hub.docker.com/_/python)

## Patch versions

::: warning Not officially supported!
While we allow users to specify patch versions for this service, they are not *officially* supported, so if you use one, YMMV.
:::

To use a patch version, you can do something as shown below:

```yaml
services:
  myservice:
    type: python:3.5.6
```

But make sure you use one of the available [patch tags](https://hub.docker.com/_/python/tags) for the underlying image we are using.

