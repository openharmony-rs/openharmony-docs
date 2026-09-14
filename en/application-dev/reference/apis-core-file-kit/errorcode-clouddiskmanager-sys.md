# Cloud Disk Management Error Codes (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34400001 Invalid Argument

**Error Message**

Invalid argument.

**Description**

The input parameter is invalid.

**Possible Causes**

The file path is empty, is not an absolute path, or contains invalid path segments (for example, ".." or "."), or an enum parameter is out of the allowed range.

**Solution**

Check and correct the input parameters, and then try again.

## 34400003 IPC Failed

**Error Message**

IPC communication failed

**Description**

IPC failed.

**Possible Causes**

The called service does not exist.

**Solution**

Check whether the service is started.

## 34400014 System Internal Error

**Error Message**

Temporary failure, Retry is recommended (e.g., network issues).

**Description**

Internal error.

**Possible Causes**

Network communication is abnormal, and data fails to be written to the database.

**Solution**

Retry by the current application.

## 34400015 Cloud Disk Not Allowed

**Error Message**

Cloud disk is not allowed on this device.

**Description**

The cloud disk is not allowed on the current device.

**Possible Causes**

The cloud disk is not allowed on the current device.

**Solution**

The third-party cloud disk application displays a dialog box, indicating that the cloud disk is not allowed on the current device.

## 34400017 Not a Placeholder File

**Error Message**

The target path is not a placeholder file.

**Description**

The target path is not a placeholder file.

**Possible Causes**

A hydration or dehydration API is called on a common file (a file not marked as a placeholder).

**Solution**

Ensure that the target file is a placeholder file created by a third-party cloud disk application before calling the API.

## 34400019 Hydration in Progress

**Error Message**

Hydration in progress.

**Description**

An in-progress hydration task already exists for the target file.

**Possible Causes**

Hydration is started again on a file whose hydration task is not completed or cancelled, or the dehydration API is called while hydration is in progress.

**Solution**

Wait until the hydration is complete, or cancel the hydration task first (by setting **callbackType** to **CANCEL_FETCH_DATA** when calling hydratePlaceholder) before performing the operation.

## 34400021 Callback Table Not Registered

**Error Message**

The callback table is not registered.

**Description**

The callback table of the cloud disk application is not registered.

**Possible Causes**

The target path is not within any registered sync root directory, or the third-party cloud disk application corresponding to the sync root of the target path has not registered a callback table.

**Solution**

Ensure that the target path is within a registered sync root directory and that the corresponding third-party cloud disk application has registered a callback table.

## 34400028 Placeholder Not Fully Hydrated

**Error Message**

The placeholder file is not fully hydrated.

**Description**

The placeholder file is not fully hydrated.

**Possible Causes**

The dehydration API is called on a placeholder file that is unhydrated or partially hydrated.

**Solution**

Call hydratePlaceholder to complete the hydration before dehydration.

## 34400029 Dehydration Denied

**Error Message**

The application denied placeholder dehydration.

**Description**

The third-party cloud disk application denied the dehydration authorization.

**Possible Causes**

Before dehydration, the system sends a dehydration authorization request to the third-party cloud disk application, and the application disallows the dehydration (for example, the file is being used on the cloud).

**Solution**

Respect the authorization result of the cloud disk application and do not perform the dehydration.

## 34400031 Already Fully Hydrated

**Error Message**

The placeholder file is already fully hydrated.

**Description**

The placeholder file is already fully hydrated and does not need to be hydrated again.

**Possible Causes**

Hydration is started again on a fully hydrated placeholder file.

**Solution**

No action is required. The file content is already on the local device.

## 34400032 No Hydration in Progress

**Error Message**

No hydration task is in progress for the target file.

**Description**

No in-progress hydration task exists for the target file.

**Possible Causes**

When hydratePlaceholder is called with **callbackType** set to **CANCEL_FETCH_DATA**, no in-progress hydration task exists for the target file.

**Solution**

No action is required.

## 34400034 Hydration Task Limit Reached

**Error Message**

The number of active placeholder hydration tasks has reached the limit.

**Description**

The number of active hydration tasks has reached the limit.

**Possible Causes**

The number of active hydration tasks of a single cloud disk application reaches five, or the global number of active hydration tasks reaches ten.

**Solution**

Wait until some hydration tasks are completed or cancelled, and then try again.
