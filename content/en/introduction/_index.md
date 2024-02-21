---
title: "Introduction"
linkTitle: "Introduction"
weight: 1
description: >
  LocalStack Snowflake emulator allows you to develop and test your Snowflake data pipelines entirely on your local machine!
cascade:
  type: docs
aliases:
  - /get-started/
hide_readingtime: true
---

[LocalStack](https://localstack.cloud/) is a cloud service emulator that runs in a single container on your laptop or in your CI environment. LocalStack Snowflake emulator replicates the functionality of a real Snowflake instance, allowing you to perform operations without an internet connection or a Snowflake account. This is valuable for locally developing and testing Snowflake data pipelines without incurring costs.

LocalStack Snowflake emulator supports the following features:

* [**Basic operations** on warehouses, databases, schemas, and tables](https://docs.snowflake.com/en/developer-guide/python-connector/python-connector-example)
* [**Storing files** in user/data/named **stages**](https://docs.snowflake.com/en/user-guide/data-load-local-file-system-create-stage)
* [**Snowpark** libraries](https://docs.snowflake.com/en/developer-guide/snowpark/python/index)
* [**Snowpipe** streaming with **Kafka connector**](https://docs.snowflake.com/en/user-guide/data-load-snowpipe-streaming-kafka)
* [**JavaScript and Python UDFs**](https://docs.snowflake.com/en/developer-guide/udf/javascript/udf-javascript-introduction)
* ... and more!

Integrating the LocalStack Snowflake emulator into your existing CI/CD pipeline allows you to run integration tests and identify issues early, reducing surprises during production deployment. Check our [Feature Coverage]({{< ref "coverage" >}}) page for a comprehensive list of supported APIs.
