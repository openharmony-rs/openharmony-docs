# Distributed Data Object Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @lvcong_oh-->
<!--Designer: @yuchaozhng-->
<!--Tester: @logic42; @hanjiawei-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=7f0249fa78f26df558bf1bb1399934cbda3430c2 translatedAt=2026-09-04T03:16:26.494Z pushedAt=2026-09-09T09:11:03.695Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 15400001 Failed to Create the In-Memory Database

**Error Message**

Failed to create the in-memory database.

**Description**

This error code is reported if the in-memory database creation fails.

**Possible Causes**

The same session ID is set for another distributed data object.

**Solution**

Use [genSessionId](js-apis-data-distributedobject.md#distributeddataobjectgensessionid) to generate a random **sessionId**, and avoid using the same **sessionId** as other distributed data objects.

## 15400002 Incorrect Parameter

**Error Message**

Parameter error.

**Description**

1. This error code is reported if the **assetKey** parameter is invalid. For example, the value is an empty string ("").

2. This error code is reported if the **uri** parameter is invalid. For example, the value is an empty string ("").

3. The **uris** parameter is invalid. For example, the **uris** array is empty or the number of elements in the array is greater than 50.

**Possible Causes**

1. The property name corresponding to the asset type in the distributed data object is invalid. For example, it is set to **null**, **undefined**, or **''** (empty string).

2. The distributed URI required by the asset to be set is invalid. For example, it is set to **null**, **undefined**, or **''** (empty string).

3. The **uris** array for storing the asset to be set is empty or the number of elements in the array is greater than 50.

4. One or more URIs in the **uris** array for storing the asset to be set are invalid. For example, they are set to **null**, **undefined**, or **''** (empty string).

**Solution**

1. Define a correct property name, for example, **'file'**.

2. Define a correct distributed URI, for example, **"file://docs/storage/Users/username/tmp.txt"**.

3. Pass in correct distributed URIs in the **uris** array, with a valid count of [1, 50], for example, **["file://docs/storage/Users/username/tmp.txt", "file://com.example.demo/data/storage/el2/base/files/test.txt"]**.

4. Ensure that each URI in the **uris** array is a correct distributed path.

## 15400003 sessionId Already Set

**Error Message**

The sessionId of the distributed object has been set.

**Description**

This error code is reported if **sessionId** of the distributed data object has been set.

**Possible Causes**

The **sessionId** has been set for the distributed data object.

**Solution**

Use [setSessionId](js-apis-data-distributedobject.md#setsessionid9-2) to cancel the existing **sessionId** and then set the asset or asset array.