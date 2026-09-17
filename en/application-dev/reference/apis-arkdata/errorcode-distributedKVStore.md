# Distributed KV Store Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=428575b0823198d70f5f0fcb1a677526877beaa9 translatedAt=2026-09-15T11:46:49.608Z pushedAt=2026-09-16T07:50:15.713Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 15100000 Invalid Parameter

**Error Message**

Parameter error. Possible causes:
1. Mandatory parameters are left unspecified.
2. Incorrect parameter types.
3. Parameter verification failed.

**Error description**

This error code is reported if the arguments are invalid.

**Possible Causes**

The input arguments do not meet the API requirements, such as the value range, length, and format.

**Solution**

Refer to the API parameter description and change the parameters to valid values.

## 15100001 Maximum Number of Subscriptions or Result Sets Exceeded

**Error Message**

Over max limits.

**Description**

The number of database subscriptions or open result sets exceeds the maximum supported limit. The current maximum limit is 8 for both.

**Possible Causes**

1. When [on('dataChange')](js-apis-distributedKVStore.md#ondatachange) is called to subscribe to database changes, the number of subscriptions to the database has exceeded the maximum limit of 8.
2. When [getResultSet](js-apis-distributedKVStore.md#getresultset) is called to obtain a database result set, the number of currently open result sets of the database exceeds the maximum limit of 8.

**Solution**

1. If the number of subscriptions to the database has exceeded the maximum limit when [on('dataChange')](js-apis-distributedKVStore.md#ondatachange) is called to subscribe to database changes, call [off('dataChange')](js-apis-distributedKVStore.md#offdatachange) to cancel some subscriptions to the database and try again.
2. If the number of currently open result sets of the database exceeds the maximum limit when [getResultSet](js-apis-distributedKVStore.md#getresultset) is called to obtain a database result set, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) to close some open result sets and try again.

## 15100002 Parameter Configuration Changes

**Error Message**

Open existed database with changed options.

**Description**

When [getKVStore](js-apis-distributedKVStore.md#getkvstore) is called to open an existing database, the **options** parameter passed in is inconsistent with the **options** parameter used when the database was created.

**Possible Causes**

The possible causes are as follows:
1. An existing **storeId** is used to create a KV store.
2. You want to change the **options** parameter of a KV store.

**Solution**

1. When creating a KV store, do not use a duplicate **storeId**.
2. Currently, the **options** parameter of a KV store cannot be changed. To apply the change, delete the KV store and create a KV store with the required **options** settings.

## 15100003 KV Store Corrupted

**Error Message**

Database corrupted.

**Description**

This error code indicates that the database is corrupted when APIs such as [put](js-apis-distributedKVStore.md#put), [delete](js-apis-distributedKVStore.md#delete), [get](js-apis-distributedKVStore.md#get), and [sync](js-apis-distributedKVStore.md#sync) are called.

**Possible Causes**

The target KV store is corrupted.

**Solution**

1. Restore the KV store from a backup file.
2. If no backup file is available, delete the corrupted KV store and create a new one.

## 15100004 Failed to Find Data

**Error Message**

Not found.

**Description**

This error code indicates that no related data is found when APIs such as [deleteKVStore](js-apis-distributedKVStore.md#deletekvstore), [sync](js-apis-distributedKVStore.md#sync), and [get](js-apis-distributedKVStore.md#get) are called.

**Possible Causes**

When no related data is found during operations such as deleting a database, querying data, or synchronizing data, the possible causes are as follows:
1. The KV store to delete does not exist or has been deleted.
2. The data queried does not exist or has been deleted.
3. The KV store specified for the data synchronization operation does not exist or has been deleted.

**Solution**

1. Before deleting a KV store, check that the KV store exists.
2. When querying data in a KV store, check whether the query keywords are correct.
3. Before synchronizing data, check that the related KV store is available.

## 15100005 KV Store or Result Set Closed

**Error Message**

Database or result set already closed.

**Description**

This error code indicates that the database or query result set is in the closed state when an API related to the database or query result set is called.

**Possible Causes**

The KV store or result set is closed manually before the operation.

**Solution**

1. Obtain the KV store and try again.
2. Obtain the result set and try again.

## 15100006 Failed to Update the Database Encryption Key

**Error Message**

Failed to update the key.

**Error description**

Failed to update the database encryption key when calling the [rekey](js-apis-distributedKVStore.md#rekey) API.

**Possible Causes**

1. The database was not created in encrypted mode (that is, **encrypt** is set to **false**) when the [getKVStore](js-apis-distributedKVStore.md#getkvstore) API was called to create it.
2. An internal error occurred during the key update.

**Solution**

1. Before using the [rekey](js-apis-distributedKVStore.md#rekey) API to update the key of an encrypted database, ensure that the current database is an encrypted database (that is, **encrypt** is set to **true** when the [getKVStore](js-apis-distributedKVStore.md#getkvstore) API is called to create the database).
2. Retry updating the key.