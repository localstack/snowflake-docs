---
title: "Initialization Hooks"
linkTitle: "Initialization Hooks"
weight: 17
description: Writing SQL scripts to initialize your Snowflake emulator
---
 
## Introduction

LocalStack for Snowflake supports automatically executing `*.sf.sql` files via [Init Hooks](https://docs.localstack.cloud/references/init-hooks/) when mounted into the Docker container. A script can be added to one of these stages in the lifecycle:

-   `BOOT`: the container is running, but LocalStack hasn’t started
-   `START`: the Python process is running, and LocalStack is starting
-   `READY`: LocalStack is ready for requests
-   `SHUTDOWN`: LocalStack is shutting down

A script can be in one of four states: `UNKNOWN`, `RUNNING`, `SUCCESSFUL`, or `ERROR`. By default, scripts are in the `UNKNOWN` state when first discovered.

## Getting started

To begin, create a script called `test.sf.sql` with the following SQL statements:

```sql
CREATE DATABASE foobar123;
CREATE DATABASE test123;
SHOW DATABASES;
```

Mount the script into `/etc/localstack/init/ready.d/` using Docker Compose or the `localstack` CLI:

{{< tabpane >}}
{{< tab header="docker-compose.yml" lang="yml" >}}
version: "3.8"

services:
  localstack:
    container_name: "${LOCALSTACK_DOCKER_NAME:-localstack-main}"
    image: localstack/snowflake
    ports:
      - "127.0.0.1:4566:4566"
      - "127.0.0.1:4510-4559:4510-4559"
      - "127.0.0.1:443:443"
    environment:
      - LOCALSTACK_AUTH_TOKEN=${LOCALSTACK_AUTH_TOKEN:?}
      - DEBUG=1
    volumes:
      - "/path/to/test.sf.sql:/etc/localstack/init/ready.d/test.sf.sql"  # ready hook
      - "${LOCALSTACK_VOLUME_DIR:-./volume}:/var/lib/localstack"
      - "/var/run/docker.sock:/var/run/docker.sock"
{{< /tab >}}
{{< tab header="CLI" lang="bash" >}}
# DOCKER_FLAGS are additional parameters to the `docker run` command of localstack start

DOCKER_FLAGS='-v /path/to/test.sf.sql:/etc/localstack/init/ready.d/test.sf.sql' DEBUG=1 localstack start
{{< /tab >}}
{{< /tabpane >}}

Start the Snowflake emulator, and the following logs will appear:

```bash 
DEBUG --- [et.reactor-0] s.analytics.handler        : REQ: POST /queries/v1/query-request {"sqlText": "CREATE DATABASE foobar123", ...
DEBUG --- [et.reactor-0] s.analytics.handler        : REQ: POST /queries/v1/query-request {"sqlText": "CREATE DATABASE test123", ...
DEBUG --- [et.reactor-0] s.analytics.handler        : REQ: POST /queries/v1/query-request {"sqlText": "SHOW DATABASES", ...
```
