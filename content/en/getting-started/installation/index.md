---
title: "Installation"
linkTitle: "Installation"
weight: 1
description: Basic installation guide to get started with the LocalStack Snowflake emulator
---

## Introduction

You can set up the LocalStack Snowflake emulator by utilizing LocalStack's Extension mechanism. There are two methods for installing the LocalStack Snowflake emulator:

- [Snowflake Docker image](https://hub.docker.com/r/localstack/snowflake)
- [LocalStack Extension mechanism](https://docs.localstack.cloud/user-guide/extensions/)

{{<alert type="info">}}
Before starting, ensure you have a valid `LOCALSTACK_AUTH_TOKEN` to access the LocalStack Snowflake emulator. Refer to the [Auth Token guide](https://docs.localstack.cloud/getting-started/auth-token/) to obtain your Auth Token and specify it in the `LOCALSTACK_AUTH_TOKEN` environment variable.
{{</alert>}}

## Snowflake Docker image

You can use the Snowflake Docker image to run the LocalStack Snowflake emulator. The Snowflake Docker image is available on the [LocalStack Docker Hub](https://hub.docker.com/r/localstack/snowflake). To pull the Snowflake Docker image, execute the following command:

{{< command >}}
$ docker pull localstack/snowflake
{{< / command >}}

You can start the Snowflake Docker container using the following methods:

1. [`localstack` CLI](https://docs.localstack.cloud/getting-started/installation/#localstack-cli)
2. [`docker` CLI](https://docs.docker.com/get-docker/)
2. [Docker Compose](https://docs.docker.com/compose/install/)

### `localstack` CLI

To start the Snowflake Docker container using the `localstack` CLI, execute the following command:

{{< command >}}
$ export LOCALSTACK_AUTH_TOKEN=<your_auth_token>
$ IMAGE_NAME=localstack/snowflake localstack start
{{< / command >}}

### `docker` CLI

To start the Snowflake Docker container using the `docker` CLI, execute the following command:

{{< command >}}
$ docker run \
    --rm -it \
    -p 4566:4566 \
    -e LOCALSTACK_AUTH_TOKEN=${LOCALSTACK_AUTH_TOKEN:?} \
    localstack/snowflake
{{< / command >}}

### Docker Compose

Create a `docker-compose.yml` file with the specified content:

```yaml
version: "3.8"

services:
  localstack:
    container_name: "localstack-main"
    image: localstack/snowflake
    ports:
      - "127.0.0.1:4566:4566"
    environment:
      - LOCALSTACK_AUTH_TOKEN=${LOCALSTACK_AUTH_TOKEN:?}
    volumes:
      - "./volume:/var/lib/localstack"
```

Start the Snowflake Docker container with the following command:

{{< command >}}
$ docker-compose up
{{< / command >}}

### Updating

To update the Snowflake Docker container, pull the latest image and restart the container. The `latest` tag is the nightly build of the Snowflake Docker image.

## LocalStack Extension mechanism

The LocalStack Extension mechanism allows you to install and manage extensions for LocalStack. Extensions are packaged as Python applications, and can be installed using:

1. [`localstack` CLI](https://docs.localstack.cloud/getting-started/installation/#localstack-cli)
2. [Docker Compose](https://docs.docker.com/compose/install/)

### `localstack` CLI

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

### Docker Compose

To install the LocalStack Snowflake emulator using Docker Compose, use the `EXTENSION_AUTO_INSTALL` environment variable for automatic extension installation. Create a `docker-compose.yml` file with the specified content:

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

### Updating

To update the LocalStack Snowflake emulator using the `localstack` CLI, uninstall and install the extension again:

{{< command >}}
$ localstack extensions uninstall localstack-extension-snowflake
$ localstack extensions install localstack-extension-snowflake
{{< / command >}}

For Docker Compose, update the extension by restarting the LocalStack container.

## Troubleshooting

### How to check if the LocalStack Snowflake emulator is running?

You can check if the LocalStack Snowflake emulator is running by executing the following command:

{{< command >}}
$ curl -d '{}' snowflake.localhost.localstack.cloud:4566/session
{"success": true}
{{< / command >}}

## Next steps

Now that the LocalStack Snowflake emulator is installed, you can use it for developing and testing your Snowflake data pipelines. Refer to our [Quickstart]({{< ref "quickstart" >}}) guide to get started.
