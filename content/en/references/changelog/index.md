---
title: "Changelog"
linkTitle: "Changelog"
weight: 2
description: >
  Changelog for the latest releases of the LocalStack for Snowflake
cascade:
  type: docs
hide_readingtime: true
---

### 0.3.0
- Add support for multi-account setups
- Add initial support for Java UDFs
- Add initial support for native apps and `APPLICATION PACKAGEs`
- Add support for row access policies
- Add support for AVRO file format
- Add support for `ALTER STAGE` and `ALTER STREAM` statements
- Enhance `SHOW COLUMNS/SCHEMAS` feature parity
- Add support for `EQUAL_NULL` and variant type check functions
- Add support for `ARRAY_REVERSE` function
- Add support for `DESCRIBE/SHOW SEQUENCES`
- Enhance timestamp handling and timezone support
- Add support for metadata columns in JSON
- Add support for `INSERT OVERWRITE` queries
- Support ZTSD compression
- Enhance `TO_CHAR` with date and number formatting
- Support dropping multiple columns in single `ALTER` statement
- Add support for TIMEZONE session parameter
- Make default user and password configurable
- Fix various timestamp and timezone-related issues
- Improve query performance by re-using PG connections per session
- Enhance parity for comparison of VARIANTs and JSON objects
- Enhance column aliasing for joins
- Fix type mapping for rowtype metadata to enhance compatibility with .NET clients
- Cast `INSERT INTO` arguments to target type
- Add support for `REGEXP_SUBSTR` function
- Prohibit Postgres specific data types
- Add `HEADER` and `FIELD_OPTIONALLY_ENCLOSED_BY` support for COPY INTO
- Support subquery in copy into location
- Support not equal operator
- Enhance parity for $N references in WHERE clauses
- Increase identifiers length to 255 char
- Improve JDBC driver compatibility
- Support LS alias to LIST files from stages

### 0.2.5
- Change storage integration to not be associated with DB/schema
- Add enhanced support for SHOW ROLES and USE ROLE
- Enhance parity for COUNT(..) with NULL values
- Add multiple statements support
- Fix staging issues with parsing
- Enhance logic for timestamp assignments in MERGE INTO queries
- Add proper passing of stage parameters and validations
- Add support for `SYSTEM$CLIENT_VERSION_INFO`/`OBJECT_CONSTRUCT_KEEP_NULL`/`TIMESTAMPADD`/`DATEADD`/`TIMEADD` functions
- Fix timestamp_ltz comparison operators issue
- Fix INSERT result count type
- Show tables metadata/information for dynamic tables
- Include Snowflake emulator version in the logs
- Update web app layout
- Enhance parity for NUMBER/FIXED data types in JDBC results
- Add support for querying from `INFORMATION_SCHEMA.TABLES`
- Fix Arrow encoding for large decimal numeric values
- Fix session for /api/v2/statements endpoint
- Improve file formats handling in COPY INTO
- Enhance parity for COPY INTO with multiple stage files
- Update metadata for integer
- Enhance parity around selecting NULL values for DATE columns
- Add initial support for materialized views
- Add format parameter for `TO_TIMESTAMP` function
- Add support for async execution of multi-statement queries
- Add support for patterns in select from stages
- Allow table column projections for COPY INTO queries from stage files
- Add support for numeric operators with mixed/variant types
- Add initial support for `MAP` data type and util functions
- Create `INFORMATION_SCHEMA.FUNCTIONS` table
- Add support for querying metadata filename in select from stage statements
- Enhance parity for primary/foreign keys
- Add support for IF EXISTS clauses in ALTER COLUMN queries
- Add initial support for user-defined transaction management

### 0.2.4
- Support `POWER`/`POW`/`DIV0NULL`/`IFNULL` functions
- Add support for COPY INTO location
- Add initial support for table/database clones
- Establish parity with snowflake when csv imports
- Allow binding multiple values
- Fix database and schema names in copy into table
- Fix `executeUpdate` in JDBC
- Support `ORDER` and `NOORDER` from AUTOINCREMENT column def
- Add initial logic and tests for replicating resources between accounts
- Convert empty csv values to null
- Add support and tests for `LATERAL` queries
- Add initial support for EXECUTE IMMEDIATE
- Add initial support for tags
- Add identifier support to SELECT queries
- Fix inserting timestamp values correctly
- Fix timestamps in insert for current_timestamp
- Add support for init scripts
- Fix handling timestamp values on update
- Add support for `DESCRIBE STAG`
- Add initial support for storage integrations
- Enhance parity of `TIMESTAMP_LTZ`
- Create clone db using identifiers
- Add mock support for replication databases to fix TF issues
- Fix logic for setting session parameters
- Add support for some extended GRANT statements
- Support `ALTER SEQUENCE`
- Support creating stages with storage integrations
- Terraform create database fixes
- Improve general error handling
- Add initial support for `SHOW GRANTS TO/OF`

### 0.2.3
- Add initial support for `OBJECT_KEYS`/`PARSE_IP`/`DESCRIBE FUNCTION` functions
- Add support for various functions including `DATE_TRUNC`, `NVL2`, `LEAST`, `GREATEST`, and more
- Enhance parity for creation/deletion of schemas with fully qualified names
- Enhance parity for inserting timestamps with subsecond precision
- Enhance parity for CTAS with nested subqueries
- Enhance parity for id placeholders in JDBC prepared statements
- Enhance parity for metadata queries and schema lookup
- Adjust `MIN_BY`/`MAX_BY` aggregate functions
- Properly extract db/schema parameters for JDBC connections
- Implement trigonometric and hyperbolic functions
- Add support for GET stage files

### 0.2.2
- Add initial support for hybrid tables and dynamic tables
- Add support for `OBJECT_CONSTRUCT_KEEP_NULL`/`AS_DOUBLE`/`AS_INTEGER`/`AS_NUMBER`/`AS_CHAR`
- Add `/result` API endpoint to retrieve query results
- Track original types in internal VARIANTs
- Enhance parity for `SHOW WAREHOUSES` queries
- Support for `SHOW TASKS`
- Enhance parsing of stage params
- Fix selection of columns when querying stage files
- Automatically adjust PG JIT support if LLVM libs are missing
- Enhance custom JSON parsing to allow escaped characters
- Enhance parity of `TIMESTAMP_LTZ` for Flyway compatibility

### 0.2.1
- Add initial support for Iceberg tables
- Add initial support for external volumes and Snowflake pipes
- Support `LIST`/`REMOVE` queries for staged files
- Support `SHOW PIPES` queries
- Support `COPY GRANTS` in `CREATE TABLE` queries
- Add multiple new SQL functions
- Implement `RANK`/`DENSE_RANK`
- Implement various conversion functions
- Enhance logic for `TO_CHAR`
- Support window queries with `QUALIFY`
- Support `COUNT_IF` aggregate functions
- Make `CREATE SERVER` queries idempotent
- Fix compatibility issues
- Add MUI data-grid for results table in UI
- Add squashing of Docker image to reduce size

### 0.2.0
- Support various SQL functions (`BITAND`, `FLATTEN`, `RANDOM`, etc.)
- Add Snowflake proxy request handler
- Add initial version of simple UI view
- Fix execution of CTAS queries with UNION selects
- Fix logic for PUT file uploads
- Support parsing incomplete JSON
- Enhance support for TABLESAMPLE queries
- Add initial support for temporary and transient tables
- Add Snowflake v2 SQL APIs
- Fix `describeOnly` `INSERT` queries

### 0.1.26
- Support `CONVERT_TIMEZONE`, `IFF` SQL functions
- Implement `ALTER WAREHOUSE` as no-op
- Implement time functions
- Enhance JDBC driver compatibility
- Fix Arrow encoding
- Support SQL queries from within JS UDFs
- Add various performance improvements
- Implement additional date functions
- Add support for loading data from public S3 buckets

### 0.1.25
- Enhance support for various SHOW queries
- Add initial persistence support for Snowflake store
- Enhance parity for timestamp types
- Fix SHOW PARAMETERS for Terraform compatibility
- Set up CI build for Docker image

### 0.1.24
- Enhance parity around user-defined PROCEDUREs
- Fix upper-casing for various functions
- Enhance support for UNIQUE column constraints
- Add initial support for cross-DB resource sharing

### 0.1.23
- Add initial simple scheduler to periodically run tasks

### 0.1.22
- Fix query transforms for `ADD COLUMN` queries
- Fix wrapping of `VALUES` subquery in braces
- Add initial CRUD support for `TASK`s
- Support `DROP PRIMARY KEY` queries
- Migrate use of `localstack.http` to `rolo`

### 0.1.21
- Add support for consuming table stream records via DML statements

### 0.1.20
- Initial simple support for table streams
- Add support for `SHOW DATABASES`, `SHOW VIEWS`
- Enhance parity for Arrow results
- Fix various identifier and query issues

### 0.1.19
- Return `SELECT` results in arrow format for pandas compatibility
- Add `add_months` function
- Fix UDFs with raw expressions
- Upgrade to Postgres v15
- Various parity and performance improvements

### 0.1.18
- Add support for various array and aggregation functions
- Enhance `FILE FORMAT` operations
- Fix `CTAS` queries
- Support `INFER_SCHEMA(..)` for parquet files
- Improve identifier handling

### 0.1.17
- Support creation/deletion of stages
- Add `IS_ARRAY` function
- Remove `DuckDB` based `DB` engine
- Refactor codebase to use `QueryProcessor` interface
- Enhance column name handling

### 0.1.16
- Add support for `SHOW PROCEDURES` and `SHOW IMPORTED KEYS`
- Add basic support for session parameters

### 0.1.15
- Fix result type conversation for `GET_PATH(..)` util function

### 0.1.14
- Enhance parity around `SHOW` queries
- Add more array util functions
- Fix `STRING_AGG` functionality

### 0.1.13
- Support `CURRENT_*` functions
- Enhance `LISTAGG` for distinct values
- Add test for `JS` UDFs with exports

### 0.1.12
- Cast params for `string_agg`/`listagg`
- Fix parity for upper/lowercase names

### 0.1.11
- Enhance parity for array aggregation functions
- Improve timestamp timezone handling
- Add case-sensitive identifier tracking

### 0.1.10
- Add query transforms for `CLUSTER BY`
- Add `SF_S3_ENDPOINT` config
- Various parity fixes

### 0.1.9
- Add support for `Python` UDFs
- Enhance function creation parity
- Add analytics setup

### 0.1.8
- Add `SF_LOG` config for request/response trace logging

### 0.1.7
- Add initial support for `JavaScript` UDFs
- Enhance DB/table creation responses
- Improve streaming logic

### 0.1.6
- Introduce session state for DB/schema retention
- Support async queries and `result_scan(..)`

### 0.1.5
- Enhance `DESCRIBE TABLE` results
- Support `MIN_BY`/`MAX_BY` aggregate functions

### 0.1.4
- Add logic to parse and replace `DB` references in queries

### 0.1.3
- Add `DBEngine` abstraction
- Add experimental support for `duckdb`
- Enhance `JSON` query support

### 0.1.2
- Add CSV file ingestion from Snowflake stage to table

### 0.1.1
- Initial support for `Kafka` connector
- Add `snowpipe`/streaming APIs

### 0.1.0
- Initial release of the extension
