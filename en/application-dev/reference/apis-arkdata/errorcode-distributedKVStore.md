# Distributed KV Store Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 15100000 Invalid Parameter

**Error Message**

Parameter error. Possible causes:
1. Mandatory parameters are left unspecified.
2. Incorrect parameter types.
3. Parameter verification failed.

**Description**

The parameter is invalid.

**Possible Causes**

The input arguments do not meet the API requirements, such as the value range, length, and format.

**Solution**

Modify the parameters to values that meet the requirements by referring to the API parameter description.

## 15100001 Subscription Count or Result Set Count Reaches the Limit

**Error Message**

Over max limits.

**Description**

The number of KV store subscriptions or the number of opened result sets reaches the upper limit 8.

**Possible Causes**

1. When the [on('dataChange')](js-apis-distributedKVStore.md#ondatachange) API is called to subscribe to KV store changes, the number of KV store subscriptions exceeds the upper limit 8.
2. When the [getResultSet](js-apis-distributedKVStore.md#getresultset) API is called to obtain the KV store result set, the number of opened result sets in the KV store exceeds the upper limit 8.

**Solution**

1. If the number of KV store subscriptions exceeds the maximum when the [on('dataChange')](js-apis-distributedKVStore.md#ondatachange) API is called, call the [off('dataChange')](js-apis-distributedKVStore.md#offdatachange) API to cancel some KV store subscriptions and try again.
2. If the number of opened KV store result sets exceeds the maximum when the [getResultSet](js-apis-distributedKVStore.md#getresultset) API is called, call the [closeResultSet](js-apis-distributedKVStore.md#closeresultset) API to close some result sets and try again.

## 15100002 Parameter Configuration Changes

**Error Message**

Open existed database with changed options.

**Description**

When the [getKVStore](js-apis-distributedKVStore.md#getkvstore) API is called to open a created KV store, the passed **options** parameter is inconsistent with that used for creating the KV store.

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

This error code is returned when the KV store is corrupted during the call of APIs such as [put](js-apis-distributedKVStore.md#put), [delete](js-apis-distributedKVStore.md#delete), [get](js-apis-distributedKVStore.md#get) and [sync](js-apis-distributedKVStore.md#sync).

**Possible Causes**

The target KV store is corrupted.

**Solution**

1. Restore the KV store from a backup file.
2. If no backup file is available, delete the corrupted KV store and create a new one.

## 15100004 Failed to Find Data

**Error Message**

Not found.

**Description**

Related data is not found when [deleteKVStore](js-apis-distributedKVStore.md#deletekvstore), [sync](js-apis-distributedKVStore.md#sync), or [get](js-apis-distributedKVStore.md#get) is called.

**Possible Causes**

The possible causes are as follows:
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

The KV store or result set to operate is already closed.

**Possible Causes**

The KV store or result set is closed manually before the operation.

**Solution**

1. Obtain the KV store and try again.
2. Obtain the result set and try again.

## 15100006 Failed to Update the KV Store Encryption Key

**Error Message**

Failed to update the key.

**Description**

Failed to call the [rekey](js-apis-distributedKVStore.md#rekey) API to update the KV store encryption key.

**Possible Causes**

1. When the [getKVStore](js-apis-distributedKVStore.md#getkvstore) API is called to create a KV store, the encryption mode is not used (that is, the value of **encrypt** is **false**).
2. An internal error occurs during the key update.

**Solution**

1. Before calling the [rekey](js-apis-distributedKVStore.md#rekey) API to update the encryption key, ensure that the current KV store is encrypted. That is, when the [getKVStore](js-apis-distributedKVStore.md#getkvstore) API is called to create a KV store, set **encrypt** to **true**.
2. Update the key again.
