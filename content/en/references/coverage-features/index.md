
---
title: "Feature Coverage"
linkTitle: "Feature Coverage"
weight: 1
description: >
  Overview of the implemented Snowflake features in LocalStack
cascade:
  type: docs
hide_readingtime: true
---

## Resource Types and Operations

This page provides a list of Snowflake query features (resource types and operations) that are supported in the LocalStack emulator.
The content will be updated as additional query features and functions are implemented.


### Databases
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|UNDROP|USE|
|----|----|----|----|----|----|----|----|
|**DATABASE**|✅|✅|❓|✅|✅|❓|❓|

### External Tables
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**EXTERNAL TABLE**|❓|❓|❓|❓|❓|

### File Formats
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**FILE FORMAT**|✅|✅|✅|✅|✅|

### Functions
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**FUNCTION**|❓|✅|✅|✅|❓|

### Integrations
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**INTEGRATION**|❓|❓|❓|❓|❓|

### Iceberg Tables
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|UNDROP|
|----|----|----|----|----|----|----|
|**ICEBERG TABLE**|❓|❓|❓|❓|❓|❓|

### Pipes
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**PIPE**|❓|✅|❓|✅|✅|

### Procedures
| |ALTER|CALL|CALL WITH|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|----|----|
|**PROCEDURE**|❓|❓|❓|✅|❓|✅|✅|

### Roles
| |ALTER|CREATE|DROP|GRANT|REVOKE|SHOW|USE|
|----|----|----|----|----|----|----|----|
|**ROLE**|❓|✅|✅|❓|❓|✅|❓|

### Schemas
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|UNDROP|USE|
|----|----|----|----|----|----|----|----|
|**SCHEMA**|✅|✅|❓|✅|❓|❓|❓|

### Sequences
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**SEQUENCE**|✅|✅|❓|✅|❓|

### Shares
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**SHARE**|❓|✅|❓|❓|❓|

### Stages
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**STAGE**|❓|✅|❓|✅|✅|

### Storage Integrations
| |ALTER|CREATE|
|----|----|----|
|**STORAGE INTEGRATION**|❓|✅|

### Streams
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**STREAM**|❓|✅|❓|✅|✅|

### Streamlits
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**STREAMLIT**|✅|✅|✅|✅|✅|

### Tables
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|TRUNCATE|UNDROP|
|----|----|----|----|----|----|----|----|
|**TABLE**|✅|✅|✅|✅|❓|❓|❓|

### Tags
| |ALTER|CREATE|DROP|SHOW|UNDROP|
|----|----|----|----|----|----|
|**TAG**|✅|✅|✅|✅|❓|

### Tasks
| |ALTER|CREATE|DESCRIBE|DROP|EXECUTE|SHOW|
|----|----|----|----|----|----|----|
|**TASK**|✅|✅|❓|✅|❓|✅|

### Users
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**USER**|✅|✅|❓|✅|✅|

### Views
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|
|----|----|----|----|----|----|
|**VIEW**|❓|✅|❓|✅|❓|

### Warehouses
| |ALTER|CREATE|DESCRIBE|DROP|SHOW|USE|
|----|----|----|----|----|----|----|
|**WAREHOUSE**|✅|✅|❓|✅|✅|❓|
