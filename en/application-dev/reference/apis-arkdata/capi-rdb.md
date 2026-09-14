# RDB
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=5132c4c17b0f557197a655ef79c7a05df0e0bea5 translatedAt=2026-09-04T03:05:36.185Z pushedAt=2026-09-09T09:11:03.682Z -->

## Overview

The relational database (RDB) supports the persistence of various structured data on a single device, as well as sync and sharing between the device and cloud.<br>The relational database defines a series of data types and supports CRUD operations on data.

**Since**: 11

## Files

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [data_asset.h](capi-data-asset-h.md)                         | Defines the data structure of an asset type.<br>An asset is a data structure that can be used in data management to store and query the attributes of a file, such as its name, absolute path, relative path, creation time, modification time, status, and occupied space. |
| [oh_cursor.h](capi-oh-cursor-h.md)                           | Defines APIs to access the result set obtained by querying the RDB store. A result set is a set of results returned after **query()** is called.|
| [oh_data_value.h](capi-oh-data-value-h.md)                   | Defines APIs and enums related to a single data value.<br>Since API version 18, **OH_ColumnType** is moved from **oh_cursor.h** to this file. This type is supported in versions earlier than API version 18 and can be used in all versions.|
| [oh_data_values.h](capi-oh-data-values-h.md)                 | Defines APIs and enums related to multiple data values.                          |
| [oh_data_values_buckets.h](capi-oh-data-values-buckets-h.md) | Defines structs, APIs, and enums related to stored data values.                |
| [oh_predicates.h](capi-oh-predicates-h.md)                   | Defines the predicates for an RDB store.                             |
| [oh_rdb_crypto_param.h](capi-oh-rdb-crypto-param-h.md)       | Defines functions and enums related to encryption parameters of the RDB store.                |
| [oh_rdb_transaction.h](capi-oh-rdb-transaction-h.md)         | Defines the functions and enums related to RDB store transactions.                           |
| [oh_rdb_types.h](capi-oh-rdb-types-h.md)                     | Defines types related to data values.                                |
| [oh_value_object.h](capi-oh-value-object-h.md)               | Defines APIs for type conversion.                                          |
| [oh_values_bucket.h](capi-oh-values-bucket-h.md)             | Defines the types of the key and value in a KV pair.                                      |
| [relational_store.h](capi-relational-store-h.md)             | Defines the APIs for managing an RDB store. The APIs that are not marked as supporting vector databases support only RDB stores. |
| [relational_store_error_code.h](capi-relational-store-error-code-h.md) | Defines the error codes used for RDB stores.                       |