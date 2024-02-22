---
title: "Snowflake Drivers"
linkTitle: "Snowflake Drivers"
weight: 1
description: Get started with connecting the LocalStack Snowflake emulator with various drivers
---

## Introduction

Snowflake Drivers enable the use of programming languages like Go, C#, and Python for developing applications that interact with Snowflake. The LocalStack Snowflake emulator facilitates testing Snowflake integration without connecting to the actual Snowflake instance. This guide provides instructions on connecting the LocalStack Snowflake emulator with various drivers.

## Snowflake Connector for Python

The Snowflake Connector for Python (`snowflake-connector-python`) is a Python library that facilitates connecting Python programs to Snowflake databases and executing operations. Utilize this connector to link to the LocalStack Snowflake emulator for testing your Snowflake integrations in Python.

To install the Snowflake Connector for Python, execute the following command:

{{< command >}}
$ pip install snowflake-connector-python
{{< /command >}}

The LocalStack Snowflake emulator operates on `snowflake.localhost.localstack.cloud` - note that this is a DNS name that resolves to a local IP address (`127.0.0.1`) to make sure the connector interacts with the local APIs. Connect to the emulator using the following Python code:

```python
import snowflake.connector as sf

conn = sf.connect(
    user="test",
    password="test",
    account="test",
    database="test",
    host="snowflake.localhost.localstack.cloud",
)
```

Subsequently, create a warehouse named `test_warehouse`, a database named `testdb`, and a schema named `testschema` using the Snowflake Connector for Python:

```python
conn.cursor().execute("CREATE WAREHOUSE IF NOT EXISTS test_warehouse")
conn.cursor().execute("CREATE DATABASE IF NOT EXISTS testdb")
conn.cursor().execute("USE DATABASE testdb")
conn.cursor().execute("CREATE SCHEMA IF NOT EXISTS testschema")
```

## Node.js Driver

The Snowflake Node.js driver facilitates connecting to Snowflake and executing operations on Snowflake databases using Node.js. Use this driver to link to the LocalStack Snowflake emulator for testing Snowflake integration.

To install the Snowflake Node.js driver, execute the following command:

{{< command >}}
$ npm install snowflake-sdk
{{< /command >}}

The LocalStack Snowflake emulator runs on `snowflake.localhost.localstack.cloud`. Connect to the emulator using the following JavaScript code:

```javascript
var snowflake = require('snowflake-sdk');
var connection = snowflake.createConnection({
    username: 'test',
    password: 'test',
    account: 'test',
    database: 'test',
    host: 'snowflake.localhost.localstack.cloud',
});
connection.connect(function(err, conn) {
  if (err) {
    console.error('Unable to connect: ' + err.message);
  } else {
    console.log('Successfully connected as id: ' + connection.getId());
  }
});
```

Execute a query to create a database named `testdb` and verify the results using the following JavaScript code:

```javascript
connection.execute({
    sqlText: 'CREATE DATABASE testdb',
    complete: function(err, stmt, rows) {
      if (err) {
        console.error('Failed to execute statement due to the following error: ' + err.message);
      } else {
        console.log('Successfully executed statement: ' + stmt.getSqlText());
      }
    }
  });
```
