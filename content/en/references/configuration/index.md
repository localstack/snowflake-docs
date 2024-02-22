---
title: "Configuration"
linkTitle: "Configuration"
weight: 3
description: >
  Overview of configuration options in LocalStack Snowflake emulator
cascade:
  type: docs
hide_readingtime: true
---

LocalStack exposes various configuration options to control its behaviour.

These options can be passed to LocalStack as environment variables like so:

{{< command >}}
$ DEBUG=1 localstack start
{{< / command >}}

## Core

Options that affect the core LocalStack Snowflake emulator functionality.

| Variable | Example Values       | Description                                                                                                 |
|----------|----------------------|-------------------------------------------------------------------------------------------------------------|
| `DEBUG`  | `0` (default) \| `1` | Flag to increase log level and print more verbose logs (useful for troubleshooting issues)                  |
| `SF_LOG` | `trace`              | Specify the log level. Currently overrides the `DEBUG` configuration. `trace` for detailed request/response |