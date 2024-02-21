---
title: "Installation"
linkTitle: "Installation"
weight: 1
description: Basic installation guide to get started with LocalStack Snowflake emulator
---

## Introduction

You can set up the LocalStack Snowflake emulator by utilizing LocalStack's Extension mechanism. There are two methods for installing the LocalStack Snowflake emulator:

1. Using the `localstack` CLI
2. Using Docker Compose

This guide provides step-by-step instructions for installing the emulator using both methods.

## Prerequisites

- [`localstack` CLI](https://docs.localstack.cloud/getting-started/installation/#localstack-cli)
- [LocalStack Web Application account](https://app.localstack.cloud/sign-up)
- [Docker](https://docs.docker.com/get-docker/)

Before starting, ensure you have a valid `LOCALSTACK_AUTH_TOKEN` to access the LocalStack Snowflake emulator. Refer to the [Auth Token guide](https://docs.localstack.cloud/getting-started/auth-token/) to obtain your Auth Token and specify it in the `LOCALSTACK_AUTH_TOKEN` environment variable.

## `localstack` CLI

To install the LocalStack Snowflake emulator using the `localstack` CLI, execute the following command:

{{< command >}}
$ localstack extensions install localstack-extension-snowflake
{{< / command >}}

Upon successful installation, you should see the output listing the installed extension.

```bash 
[20:30:06] Extension successfully installed                                                 extensions.py:86
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━┓
┃ Name                           ┃ Summary                         ┃ Version ┃ Author     ┃ Plugin name ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━┩
│ localstack-extension-snowflake │ LocalStack Extension: Snowflake │ 0.1.22  │ LocalStack │ snowflake   │
└────────────────────────────────┴─────────────────────────────────┴─────────┴────────────┴─────────────┘
```

## Docker Compose

To install the LocalStack Snowflake emulator using Docker Compose, use the `EXTENSION_AUTO_INSTALL` environment variable for automatic extension installation. Create a `docker-compose.yml` file with the specified content.

```yaml
version: "3.8"

services:
  localstack:
    container_name: "localstack-main"
    image: localstack/localstack-pro
    ports:
      - "127.0.0.1:4566:4566"
      - "127.0.0.1:4510-4559:4510-4559"
    environment:
      - LOCALSTACK_AUTH_TOKEN=${LOCALSTACK_AUTH_TOKEN:?}
      - DEBUG=1
      - EXTENSION_AUTO_INSTALL=localstack-extension-snowflake
    volumes:
      - "./volume:/var/lib/localstack"
      - "/var/run/docker.sock:/var/run/docker.sock"
```

Start the LocalStack Snowflake emulator with the following command:

{{< command >}}
$ docker-compose up
{{< / command >}}

## Updating

To update the LocalStack Snowflake emulator using the `localstack` CLI, uninstall and install the extension again:

{{< command >}}
$ localstack extensions uninstall localstack-extension-snowflake
$ localstack extensions install localstack-extension-snowflake
{{< / command >}}

For Docker Compose, update the extension by restarting the LocalStack container.

## Next steps

Now that the LocalStack Snowflake emulator is installed, you can use it for developing and testing your Snowflake data pipelines. Refer to our [Quickstart]({{< ref "quickstart" >}}) guide to get started.
