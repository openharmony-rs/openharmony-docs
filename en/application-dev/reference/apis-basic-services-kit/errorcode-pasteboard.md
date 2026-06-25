# Pasteboard Error Codes
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## Overview

This topic describes only module-specific error codes. helping developers identify and rectify problems that occur during pasteboard operations. This topic covers error codes related to index operations, capacity limits, operation conflicts, permission settings, and system exceptions.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 12900001 Index Out of Range

**Error Message**

The index is out of range.

**Description**

This error code is reported when the index passed in to the called API, such as **getRecord**, is out of range. The index should be with the range from 0 to value of **recordCount** minus 1.

**Possible Causes**

The index passed in the API is beyond the record index range of the **PasteData** object. For example, the index passed in to **getRecord** exceeds the number of records.

**Solution**

1. Check whether the index is within the valid range (0 to value of **recordCount** minus 1). The current number of records can be obtained by calling **getRecordCount()**.
2. Call the API again using a valid index.

## 12900002 Maximum Number of Records Reached

**Error Message**

The number of records exceeds the upper limit.

**Description**

This error code is reported when no new **PasteData** record can be added.

**Possible Causes**

Related records are not deleted or the number of records is not checked. This error code is reported when new records are added after the number of records has reached the maximum.

**Solution**

1. Check whether the number of **PasteData** records has reached the maximum.
2. If the number of **PasteData** records has reached the maximum, delete some records before adding new ones.

## 12900003 Another Copy or Paste Operation in Progress

Similar to the error code [27787277](#27787277-another-copy-or-paste-operation-in-progress).

**Error Message**

Another copy or paste operation is in progress.

**Description**

This error code is reported when a new copy or paste attempt is made before the previous one is completed.

**Possible Causes**

A large amount of data needs to be copied or pasted, which takes a long time. This error code is triggered when a new copy or paste attempt is made before the previous one is completed.

**Solution**

1. Before you copy or paste data, check whether the last copy or paste operation has been completed using a callback or promise.
2. Ensure that the last copy or paste operation is completed before copying or pasting data again.

## 12900004 Copy Prohibited

Similar to the error code [27787278](#27787278-copy-prohibited).

**Error Message**

Replication is prohibited.

**Description**

This error code is reported when an attempt is made to copy data that cannot be copied.

**Possible Causes**

The data is read-only and cannot be copied.

**Solution**

1. Make sure the target data allows the copy action.
2. Do not copy data that cannot be copied, for example, data loss prevention (DLP) read-only data. For details, see [About This Kit](../../security/DataProtectionKit/dlp-overview.md).

## 12900005 Request Timeout

**Error Message**

Excessive processing time for internal data.

**Description**

This error code is reported when the time spent in internal data processing exceeds the timeout.

**Possible Causes**

The data to be processed is large and consumes too much time.

**Solution**

You are advised to use asynchronous APIs instead of synchronous APIs when processing a large amount of data to prevent timeout errors.

## 12900006 Settings Already Exists

**Error Message**

Settings already exist.

**Description**

This error code is reported when the global pasteable scope to be set already exists for your application.

**Possible Causes**

The global pasteable scope of the application already exists.

**Solution**

1. Delete the existing pasteable scope settings by calling the corresponding method.
2. After confirming that the deletion is successful, call the setting method to set a new pasteable scope.

## 12900007 File Copying Failure

**Error Message**

Invalid destUri or file system error.

**Description**

This error code is reported when a file fails to be copied.

**Possible Causes**

1. The destination URI is invalid or does not exist.
2. An error occurs in the file system, for example, insufficient storage space or restricted permission.

**Solution**

1. Before copying related data, check whether the destination path is valid.
2. If the destination path is invalid, confirm the correct path.

## 12900008 Progress Startup Failure

**Error Message**

Failed to start progress.

**Description**

This error code is reported when the progress fails to be created using the default progress indicator. If no custom progress indicator is configured, the system automatically uses the default progress indicator. For details about how to customize the progress bar, see [ProgressIndicator](./js-apis-pasteboard.md#progressindicator15).

**Possible Causes**

The system thread is abnormal.

**Solution**

Check whether the pasting is successful.

1. If the pasting is successful, ignore this error code.
2. If the pasting fails, further locate the cause.
3. If the fault persists, contact technical support.

## 12900009 Progress Reporting Exception

**Error Message**

Progress exits abnormally.

**Description**

This error code is reported when progress reporting is abnormal using the default progress indicator. If no custom progress indicator is configured, the system uses the default progress indicator.

**Possible Causes**

System resources are insufficient, the UI thread is blocked, or the progress bar component is faulty.

**Solution**

1. Check the system resource status to determine whether resources, such as the memory and CPU, are insufficient.
2. Check whether the UI thread is blocked. Prevent time-consuming operations on the UI thread.
3. If the pasting is successful, ignore this error code, because it does not affect normal use.
4. If the pasting fails, contact technical support for further assistance.

## 12900010 Data Obtaining Failure

**Error Message**

System error occurred during paste execution.

**Description**

This error code is reported when the data to be pasted fails to be obtained.

**Possible Causes**

It is caused by internal system errors, such as insufficient system resources, insufficient permissions, pasteboard service exceptions, incompatible data formats, and memory shortage.

**Solution**

1. Check the app permission configuration and ensure that the necessary pasteboard access permission has been obtained.
2. Check the system resource status to determine whether resources are insufficient.
3. If the fault persists, contact technical support to obtain detailed error logs.

## 27787277 Another Copy or Paste Operation in Progress

Similar to the error code [12900003](#12900003-another-copy-or-paste-operation-in-progress).

**Error Message**

Another copy or paste operation is in progress.

**Description**

This error code is reported when a new copy or paste attempt is made before the previous one is completed.

**Possible Causes**

The copy and paste APIs are both asynchronous APIs. If the data to be copied or pasted is in large amount, the time required may be long. New copy or paste operations can be performed only after the previous operations have been completed.

**Solution**

1. Before you copy or paste data, check whether the last copy or paste operation has been completed using a callback or promise.
2. Ensure that the last copy or paste operation is completed before copying or pasting data again.

## 27787278 Copy Prohibited

Similar to the error code [12900004](#12900004-copy-prohibited).

**Error Message**

Replication is prohibited.

**Description**

This error code is reported when an attempt is made to copy data that cannot be copied.

**Possible Causes**

The data is read-only and cannot be copied.

**Solution**

1. Make sure the target data allows the copy action.
2. Make sure you only copy data that allows for copy.
