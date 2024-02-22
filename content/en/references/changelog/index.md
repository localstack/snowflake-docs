---
title: "Changelog"
linkTitle: "Changelog"
weight: 2
description: >
  Changelog for the latest releases of the LocalStack Snowflake emulator
cascade:
  type: docs
hide_readingtime: true
---

| Version   | Changes                                                                                                              |
|-----------|-----------------------------------------------------------------------------------------------------------------------|
| 0.1.23    | Add initial simple scheduler to periodically run tasks                                                              |
| 0.1.22    | Fix query transforms for `ADD COLUMN` queries; fix wrapping of `VALUES` subquery in braces for `MERGE` queries; add initial CRUD support for `TASK`s; support `DROP PRIMARY KEY` queries; migrate use of `localstack.http` to `rolo` |
| 0.1.21    | Add support for consuming table stream records via DML statements                                                      |
| 0.1.20    | Initial simple support for table streams; add support for `SHOW DATABASES`, `SHOW VIEWS`; enhance parity for Arrow results of `TIMESTAMP_NTZ` values; more refactoring into `QueryProcessor` classes; fix identifier uppercasing for `ALTER TABLE` queries; fix extraction of DB name from `CREATE SCHEMA` queries |
| 0.1.19    | Return `SELECT` results in arrow format for pandas compatibility; add `add_months` function; fix UDFs with raw expressions; upgrade to Postgres v15; distinguish internal/external `VARIANT`s; print query processors in CI logs; enable lazy installation of `plv8` extension; enhance parity around `CREATE VIEW` queries; extend analytics; return `row_count` for `UPDATE` queries; add `statementTypeId` |
| 0.1.18    | Add support for various array and aggregation functions; enhance `FILE FORMAT` operations; fix `CTAS` (Create Table AS) queries; support `INFER_SCHEMA(..)` for getting schema from parquet files; better handling of upper/lowercase identifiers |
| 0.1.17    | Support creation/deletion of stages; add `IS_ARRAY` function; remove `DuckDB` based `DB` engine; refactor codebase to use `QueryProcessor` interface; enhance proper handling of column names for table aliases |
| 0.1.16    | Add support for `SHOW PROCEDURES` and `SHOW IMPORTED KEYS`; add basic support for session parameters                      |
| 0.1.15    | Fix result type conversation for `GET_PATH(..)` util function                                                          |
| 0.1.14    | Enhance parity around `SHOW TABLES/OBJECTS/COLUMNS` queries; add more array util functions; fix `STRING_AGG` for different `DISTINCT`/`GROUP` combinations |
| 0.1.13    | Support some `CURRENT_*` functions; enhance `LISTAGG` for distinct values; add test for `JS` UDFs with exports            |
| 0.1.12    | Cast params for `string_agg`/`listagg`; more parity fixes for upper/lowercase names                                   |
| 0.1.11    | Enhance parity for array aggregation functions; enhance parity around subqueries and `timestamp` timezones; add logic to keep track of case-sensitive `db/table` identifiers |
| 0.1.10    | Add query transforms for `CLUSTER BY`; add `SF_S3_ENDPOINT` config; more parity fixes                                |
| 0.1.9     | Add support for `Python` UDFs; enhance parity around `CREATE OR REPLACE FUNCTION` queries; add analytics setup           |
| 0.1.8     | Add `SF_LOG` config to enable request/response trace logging                                                            |
| 0.1.7     | Add initial support for `Snowflake` `JavaScript` UDFs; enhance parity around responses for `DB`/`table` creation; enhancements for `Snowflake` streaming logic |
| 0.1.6     | Introduce session state to retain `DB/schema` across queries; support async queries and `result_scan(..)`              |
| 0.1.5     | Enhance parity around `DESCRIBE TABLE` results; support `MIN_BY`/`MAX_BY` aggregate functions                         |
| 0.1.4     | Add logic to parse and replace `DB` references in queries                                                                |
| 0.1.3     | Add `DBEngine` abstraction, experimental support for `duckdb`; enhance support for `JSON` queries                      |
| 0.1.2     | Add logic to ingest a `CSV` file from a `Snowflake` `stage` into a table                                               |
| 0.1.1     | Initial support for `Kafka` connector and `snowpipe`/streaming APIs                                                    |
| 0.1.0     | Initial release of the extension                                                                                      |
