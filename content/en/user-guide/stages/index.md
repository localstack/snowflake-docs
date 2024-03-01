---
title: "Stages"
linkTitle: "Stages"
weight: 7
description: Get started with Stages in LocalStack Snowflake emulator
---

## Introduction

Stages are a way to load data into Snowflake. You can use stages to load data from files in a variety of formats, including CSV, JSON, and Parquet. You can also use stages to load data from external cloud storage services, such as Amazon S3, Google Cloud Storage, and Microsoft Azure Blob Storage.

LocalStack Snowflake emulator supports stages, allowing you to load data into Snowflake using the same commands and syntax as the Snowflake service. The following operations are supported:

- [`CREATE STAGE`](https://docs.snowflake.com/en/sql-reference/sql/create-stage.html)
- [`DROP STAGE`](https://docs.snowflake.com/en/sql-reference/sql/drop-stage.html)

## Getting started

This guide is designed for users new to Stages and assumes basic knowledge of SQL and Snowflake. Start your LocalStack Snowflake emulator and connect to it using an SQL client in order to execute the queries further below.

In this guide, you will create a database and a table for storing data. You will then create a stage to load data into the table.

### Download the sample data

You can download the sample data by [right-clicking on this link](./getting-started.zip) and downloading this in your machine. Unzip the file and save the contents to a directory on your local machine.

### Create a database & table

You can create a database using the `CREATE DATABASE` command. In this example, you can create a database called `sf_tuts`:

```sql
CREATE OR REPLACE DATABASE sf_tuts;
```

Similarly, you can create a table using the `CREATE TABLE` command. In this example, you can create a table called `emp_basic` in `sf_tuts.public`:

```sql
CREATE OR REPLACE TABLE emp_basic (
   first_name STRING ,
   last_name STRING ,
   email STRING ,
   streetaddress STRING ,
   city STRING ,
   start_date DATE
   );
```

### Load data into a stage

You can now create a stage using the `CREATE STAGE` command. In this example, you can upload the CSV files to the table stage provided for `emp_basic` table.

{{< tabpane >}}
{{< tab header="Linux/macOS" lang="sql" >}}
PUT file://./employees0*.csv @sf_tuts.public.%emp_basic;
{{< /tab >}}
{{< tab header="Windows" lang="sql" >}}
PUT file://C:\temp\employees0*.csv @sf_tuts.public.%emp_basic;
{{< /tab >}}
{{< /tabpane >}}

The expected output is:

```sql
+-----------------+--------------------+-------------+-------------+--------------------+--------------------+----------+---------+
| source          | target             | source_size | target_size | source_compression | target_compression | status   | message |
|-----------------+--------------------+-------------+-------------+--------------------+--------------------+----------+---------|
| employees01.csv | employees01.csv.gz |         370 |           0 | NONE               | GZIP               | SKIPPED  |         |
| employees02.csv | employees02.csv.gz |         364 |           0 | NONE               | GZIP               | SKIPPED  |         |
| employees03.csv | employees03.csv.gz |         407 |           0 | NONE               | GZIP               | SKIPPED  |         |
| employees04.csv | employees04.csv.gz |         375 |           0 | NONE               | GZIP               | SKIPPED  |         |
| employees05.csv | employees05.csv.gz |         404 |           0 | NONE               | GZIP               | SKIPPED  |         |
+-----------------+--------------------+-------------+-------------+--------------------+--------------------+----------+---------+
```
