---
title: "Polaris Catalog"
linkTitle: "Polaris Catalog"
weight: 18
description: Get started with Polaris Catalog in LocalStack for Snowflake
---

{{< preview-notice >}}

## Introduction

Polaris Catalog is a unified data catalog that provides a single view of all your data assets across Snowflake and external sources. It enables you to discover, understand, and govern your data assets, making it easier to find and use the right data for your analytics and machine learning projects.

The Snowflake emulator supports creating Iceberg tables with Polaris catalog. Currently, [`CREATE CATALOG INTEGRATION`](https://docs.snowflake.com/en/sql-reference/sql/create-catalog-integration-open-catalog) is supported by LocalStack.

## Getting started

This guide is designed for users new to Iceberg tables with Polaris catalog and assumes basic knowledge of SQL and Snowflake. Start your Snowflake emulator and connect to it using an SQL client in order to execute the queries further below.

In this guide, you will create an Iceberg table, display the data in the Iceberg table, and drop the Iceberg table.

### Create an Iceberg table

You can create an Iceberg table using the `CREATE ICEBERG TABLE` statement. In this example, you can create an external volume called `v_demo`:

```sql
CREATE OR REPLACE EXTERNAL VOLUME v_demo
  STORAGE_LOCATIONS = (
    (
      NAME = 'aws-s3-test'
      STORAGE_PROVIDER = 'S3'
      STORAGE_BASE_URL = 's3://testbucket/'
      STORAGE_AWS_ROLE_ARN = '000000000000'
      ENCRYPTION=(TYPE='AWS_SSE_S3')
    )
  )
  ALLOW_WRITES = TRUE;
```

### Create a Catalog integration

You can then create a Catalog integration using the `CREATE CATALOG INTEGRATION` statement. In this example, you can create a catalog integration called `catalog_demo`:

```sql
CREATE CATALOG INTEGRATION catalog_demo
CATALOG_SOURCE=ICEBERG_REST
TABLE_FORMAT=ICEBERG
CATALOG_NAMESPACE='test_namespace'
REST_CONFIG=(
    CATALOG_URI='http://localhost:8181'
    CATALOG_NAME='polaris'
)
REST_AUTHENTICATION=(
    TYPE=OAUTH
    OAUTH_CLIENT_ID='root'
    OAUTH_CLIENT_SECRET='s3cr3t'
    OAUTH_ALLOWED_SCOPES=(PRINCIPAL_ROLE:ALL)
)
ENABLED=TRUE
REFRESH_INTERVAL_SECONDS=60
COMMENT='Test catalog integration';
```

### Create an Iceberg table

You can create an Iceberg table using the `CREATE ICEBERG TABLE` statement. In this example, you can create an Iceberg table called `t_demo`:

```sql
CREATE ICEBERG TABLE t_demo (c1 TEXT)
CATALOG='catalog_demo', EXTERNAL_VOLUME='v_demo', BASE_LOCATION='test/test_namespace';
```

The output should be:

```sql
+-------------------------------------------+                                    
| status                                    |
|-------------------------------------------|
| Table "t_demo" successfully created.      |
+-------------------------------------------+
```

### Show Iceberg tables

You can display the Iceberg tables using a `SELECT` query:

```sql
SELECT * FROM t_demo;
```

The output should be:

```sql
+----------+
| c1       |
|----------|
| iceberg  |
| foobar   |
| test     |
+----------+
```

### Drop Iceberg table

You can drop the Iceberg table using the `DROP ICEBERG TABLE` statement:

```sql
DROP ICEBERG TABLE t_demo;
```

The output should be:

```sql
+-------------------------------------------+  
| status                                    |
| ------------------------------------------+
| T_DEMO successfully dropped.              |
+-------------------------------------------+
```
