---
title: "Native Apps"
linkTitle: "Native Apps"
weight: 18
description: Get started with Native Apps in LocalStack for Snowflake
---

## Introduction

Snowflake Native Apps are applications built and executed directly within the Snowflake Data Cloud platform. These apps can be used to extend the capabilities of Snowflake by integrating with external services, automating workflows, and building custom data applications. These apps are developed using Snowflake-native tools (e.g., Snowflake SQL, Snowflake API, and JavaScript) and can be distributed on the Snowflake Marketplace.

The Snowflake emulator supports CRUD operations for Native Apps, allowing you to create, read, update, and delete apps using the same commands and syntax as the Snowflake service. The following operations are supported:

- [`CREATE APPLICATIONS`](https://docs.snowflake.com/en/sql-reference/sql/create-application.html)
- [`SHOW APPLICATION PACKAGES`](https://docs.snowflake.com/en/sql-reference/sql/show-application-packages.html)
- [`ALTER APPLICATION PACKAGE`](https://docs.snowflake.com/en/sql-reference/sql/alter-application-package.html)
- [`DESCRIBE APPLICATION PACKAGE`](https://docs.snowflake.com/en/sql-reference/sql/describe-application-package.html)
- [`DROP APPLICATION PACKAGE`](https://docs.snowflake.com/en/sql-reference/sql/drop-application-package.html)

## Getting started

This guide is designed for users new to Native Apps and assumes basic knowledge of SQL and Snowflake. Start your Snowflake emulator and connect to it using an SQL client in order to execute the queries further below.
 
In this guide, you will  createan Application Package, add a version to your Application Package using a manifest file, create a Native Application from that package, view and describe your Native Applications, and clean up by dropping applications and packages.

### Create an Application Package

An Application Package is a container that can hold multiple versions of your Native App code and metadata. Use the `CREATE APPLICATION PACKAGE` statement:

```sql
CREATE OR REPLACE APPLICATION PACKAGE my_first_package;
```

You can view all existing Application Packages in your environment using the `SHOW APPLICATION PACKAGES` statement:

```sql 
SHOW APPLICATION PACKAGES;
```

### Prepare a Manifest File

A manifest file describes your Native App version (e.g., name, version, comment). You typically store the manifest in a stage so that Snowflake can access it easily when creating a new app version.

Create your `manifest.yml` locally:

```yml
manifest_version: 1
version:
  name: v1
  comment: "My first native application"
```

You can then upload the manifest file to a stage:

```sql
PUT file://./manifest.yml @my_stage AUTO_COMPRESS=FALSE;
```

### Add a Version to Your Application Package

Once your manifest (and any related files) are uploaded to a stage, you can register a version with the Application Package using the `ALTER APPLICATION PACKAGE` statement:

```sql
ALTER APPLICATION PACKAGE my_first_package 
  ADD VERSION v1 
  USING '@my_stage';
```

After adding a version, you can optionally set it as the default release directive:

```sql
ALTER APPLICATION PACKAGE my_first_package 
  SET DEFAULT RELEASE DIRECTIVE VERSION = v1 PATCH = 0;
```

Use `SHOW APPLICATION PACKAGES` again to see details of your updated package:

```sql
SHOW APPLICATION PACKAGES LIKE 'MY_FIRST_PACKAGE';
```

### Create a Native Application from the Package

Next, create a Native Application that references the versioned Application Package you just set up using the `CREATE APPLICATION` statement:

```sql
CREATE OR REPLACE APPLICATION my_native_app
  FROM APPLICATION PACKAGE my_first_package;
```

### Clean up

When you no longer need your Native Application or its package, you can drop them using the `DROP APPLICATION` and `DROP APPLICATION PACKAGE` statements:

```sql
DROP APPLICATION my_native_app;
DROP APPLICATION PACKAGE my_first_package;
```
