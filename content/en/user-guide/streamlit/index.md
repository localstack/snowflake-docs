---
title: "Streamlit"
linkTitle: "Streamlit"
weight: 8
description: Get started with Streamlit in LocalStack Snowflake emulator
---

## Introduction

Snowflake provides SQL commands to create and modify a `STREAMLIT` object. Streamlit is a Python library that allows you to create web applications with simple Python scripts. With Streamlit, you can create interactive web applications without having to learn complex web development technologies.

LocalStack Snowflake emulator supports Streamlit, allowing you to create Streamlit applications using the same commands and syntax as the Snowflake service. The following operations are supported:

- `CREATE STREAMLIT`
- `SHOW STREAMLIT`
- `DESCRIBE STREAMLIT`
- `ALTER STREAMLIT`
- `DROP STREAMLIT`

## Getting started

This guide is designed for users new to Streamlit and assumes basic knowledge of SQL and Snowflake. Start your LocalStack Snowflake emulator and connect to it using an SQL client in order to execute the queries further below.

In this guide, you will create a Streamlit application, describe the Streamlit application, and drop the Streamlit application.

### Create an application

You can create a Streamlit application using the `CREATE STREAMLIT` command. In this example, you can create a Streamlit application called `testapp` with a `@teststage` stage and a `test.py` script:

```sql
+-----------------------------------------+                                     
| ?COLUMN?                                |
|-----------------------------------------|
| Streamlit TESTAPP successfully created. |
+-----------------------------------------+
1 Row(s) produced. Time Elapsed: 0.191s
```

The output shows that the Streamlit application `testapp` was successfully created.

```sql
+-----------------------------------------+                                     
| ?COLUMN?                                |
|-----------------------------------------|
| Streamlit TESTAPP successfully created. |
+-----------------------------------------+
```

### Describe the application

You can show the Streamlit application using the `DESCRIBE STREAMLIT` command. In this example, you can describe the Streamlit application `testapp`:

```sql
DESCRIBE STREAMLIT testapp;
```

The output shows the details of the Streamlit application `testapp`.

```sql
+---------+-------+---------------+-----------+-----------------+---------+------------------+---------------+
| name    | title | root_location | main_file | query_warehouse | url_id  | default_packages | user_packages |
|---------+-------+---------------+-----------+-----------------+---------+------------------+---------------|
| TESTAPP | NULL  | @teststage    | test.py   | NULL            | testurl | ...              |               |
```

### Drop the application

You can drop the Streamlit application using the `DROP STREAMLIT` command. In this example, you can drop the Streamlit application `testapp`:

```sql
DROP STREAMLIT testapp;
```

The output shows that the Streamlit application `testapp` was successfully dropped.

```sql
+-----------------------------------------+                                     
| ?COLUMN?                                |
|-----------------------------------------|
| Streamlit TESTAPP successfully dropped. |
+-----------------------------------------+
```
