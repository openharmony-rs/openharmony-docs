# ArkData Glossary
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @widecode-->
<!--Designer: @widecode-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8bddd9c7e5c9880b9d2e40955ac7c4b514506733 translatedAt=2026-09-14T08:36:00.008Z pushedAt=2026-09-15T08:03:08.118Z -->

## C

### Cross-Device Data Sync

A capability (that is, a distributed capability) that synchronizes data in an application's database to other devices in a networking environment. Based on the data lifecycle, data is classified into temporary data (using distributed data objects) and persistent data (using a relational store or a key-value store). Cross-device data sync within the same application supports only eventual consistency. For details, see [Overview of Cross-Device Application Data Sync](sync-app-data-across-devices-overview.md).

## D

### DataShare

A cross-application data sharing mechanism that provides data collaboration capabilities between data providers and data accessors. Its implementation methods include DataShareExtensionAbility, DataShareHelper, and silent data access.

### Distributed Data Object

An object that provides distributed capabilities for object-structured data, supports cross-device "global" access to variables, and implements data synchronization between devices through the `sessionId` identifier. It applies to cross-device migration and multi-device collaboration scenarios.

## E

### E-Class Encrypted Database

An encrypted database with a higher security level, used to store sensitive user information. The key is destroyed when the screen is locked and restored after the screen is unlocked. For details, see [Using an EL5 Database (ArkTS)](encrypted-estore-guidelines.md).

## F

### FULL Mode

One of the database synchronization write policies in SQLite. When data is modified each time, SQLite calls the xSync method of the underlying OS to ensure that all data is securely written to the disk. This ensures that the database is not damaged in the case of system breakdown or power failure.

For details, see SQLite [synchronous](https://sqlite.org/pragma.html#pragma_synchronous).

## K

### Key-Value Store (KV Store)

A database where data is stored in key-value pairs. It provides read/write, encryption, and backup capabilities, and supports two types: single-version databases and device-collaborative databases. It is suitable for business data storage scenarios with simple data relationships, non-relational database scenarios, and cross-device compatibility scenarios.

## P

### Predicate

A term used to define conditions for database operations, commonly applied in scenarios such as querying, updating, and deleting data.

### Preferences

A lightweight key-value data persistence capability used to store lightweight data such as application configuration information and user preferences. Data is stored in text form and loaded entirely into memory when used by an application. It supports the XML storage mode (the default storage mode, which is highly versatile, supports cross-platform use, and does not support multi-process concurrency) and the GSKV storage mode (which supports multi-process concurrency).

## R

### RelationalStore

A data persistence solution based on the SQLite component that stores data in rows and columns. It supports add, delete, modify, and query APIs and custom SQL statements, and provides features such as transactions and indexes. Vector database capabilities are supported starting from API version 18. For details, see [@ohos.data.relationalStore (RelationalStore)](../reference/apis-arkdata/arkts-apis-data-relationalStore.md).

### ResultSet

A set of query results, which allows access to the required data in flexible modes.

## S

### Security Level

An identification system for classifying data and devices. Data security labels are divided into four levels: S1 (low), S2 (medium), S3 (high), and S4 (critical), which indicate the sensitivity of data. Device security levels are divided into five levels, SL1 to SL5, depending on the security capabilities of the device. During cross-device synchronization, data can be synchronized only when the data security label is not higher than the security level of the peer device. For details, see [Access Control by Device and Data Level](access-control-by-device-and-data-level.md).

## T

### Transaction

An object used to ensure the atomicity of database operations. You can obtain a `Transaction` object through the `createTransaction` API of `RdbStore`. It provides the `commit` and `rollback` methods to ensure that multiple operations either all succeed or all fail. It supports three transaction types: `DEFERRED` (default), `IMMEDIATE`, and `EXCLUSIVE`.

## U

### Unified Data Management Framework (UDMF)

A standardized data management framework that provides a unified data language for data interaction across applications and devices. It includes Unified Type Descriptor (UTD) and Unified Data Structure (UDS). For details, see [Unified Data Definition Overview](unified-data-definition-overview.md).

## V

### Vector Store

A database that supports storing, managing, and retrieving vector data, available since API version 18. It is implemented based on a relational database and supports features such as vector indexing, data aging, and data compression. It is suitable for AI scenarios such as recommendation systems, similar image retrieval, and natural language processing.

## W

### Write Ahead Log (WAL)

One of the SQLite journal modes. Unlike the traditional rollback journal mode, it improves concurrency performance and write efficiency.

For details, see SQLite [Write-Ahead Logging](https://sqlite.org/wal.html).