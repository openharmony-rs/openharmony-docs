# Cloud Disk Management Error Codes (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=b623a2244f778d4f67b753177f0f9827b721ce9b translatedAt=2026-11-04T03:52:52.405Z pushedAt=2026-11-04T10:12:33.443Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34400001 Invalid Input Parameter

**Error Message**

The input parameter is invalid.

**Description**

The input parameter is invalid.

**Possible Causes**

The file path is empty, is not an absolute path, contains illegal path segments (such as ".." or "."), or the value of an enumeration parameter is outside the allowed range.

**Solution**

Check and correct the input parameters, and then retry.

## 34400003 IPC Failed

**Error Message**

IPC communication failed.

**Description**

IPC failed.

**Possible Causes**

The called service does not exist.

**Solution**

Check whether the service is started.

## 34400008 Sync Root Path Not Registered

**Error Message**

No sync root is registered, or the registered sync roots cannot be queried.

**Description**

The sync root path is not registered, or querying the registered sync root information fails.

**Possible Causes**

The target path is not within the scope of any registered sync root directory, or the system fails to query the registered sync root information.

**Solution**

Call [getAllSyncFolders](js-apis-file-clouddiskmanager-sys.md#getallsyncfolders)() to query the list of registered sync roots, confirm that the target path is within the scope of a sync root directory, and then retry.

## 34400010 Sync Root Path Does Not Exist

**Error Message**

The sync root path does not exist, or the target file or sync root mount path is missing during path resolution.

**Description**

The sync root path does not exist, or the target file or mount path is missing during path resolution.

**Possible Causes**

The sync root directory has been deleted or is not mounted, or the target file does not exist during path resolution.

**Solution**

Confirm that the sync root path exists and the target file path is valid, then retry.

## 34400014 System Internal Error

**Error Message**

Temporary failure. Retry is recommended (e.g., network issues).

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

## 34400017 Target Path Is Not a Placeholder File

**Error Message**

The target path is not a placeholder file.

**Description**

The target path is not a placeholder file.

**Possible Causes**

The hydration or dehydration API is called on a regular file (a file not marked as a placeholder).

**Solution**

Call [getAllSyncFolders](js-apis-file-clouddiskmanager-sys.md#getallsyncfolders)() to confirm that the target file is located within the sync root directory registered by the third-party cloud drive application and is a file created by the cloud drive application (only metadata is retained locally, with content stored on the cloud side) before calling the API.

## 34400019 Hydration Task Already in Progress

**Error Message**

A hydrate task for the target file is already pending or in progress.

**Description**

A hydration task is already in progress for the target file.

**Possible Causes**

A hydration request is initiated again for the same file before its hydration task is completed or canceled, or the dehydration API is called while hydration is in progress.

**Solution**

Wait for the hydration to complete, or first call [hydratePlaceholder](js-apis-file-clouddiskmanager-sys.md#hydrateplaceholder)() (with callbackType set to CANCEL_FETCH_DATA) to cancel the hydration task before proceeding.

## 34400020 Insufficient Available Disk Space

**Error Message**

The available disk space is insufficient, or the disk quota has been exhausted.

**Description**

The available disk space is insufficient, or the disk quota has been exhausted.

**Possible Causes**

The local disk space is insufficient when performing dehydration, or the application's disk quota has been exhausted.

**Solution**

Free up local storage space or increase the disk quota, and then retry.

## 34400021 Callback Table Not Registered

**Error Message**

The cloud disk provider's callback table is not registered, or no usable sync root matches the path.

**Description**

The cloud drive application's callback table is not registered, or there is no usable sync root matching the path.

**Possible Causes**

The target path is not within the scope of any registered sync root directory, or the third-party cloud drive application corresponding to the sync root to which the target path belongs has not registered its callback table.

**Solution**

Confirm that the target path is within the scope of a registered sync root directory, and that the corresponding third-party cloud drive application has completed callback table registration.

## 34400023 Path Parent Directory Is Not a Directory

**Error Message**

A path component that must be a directory is not a directory.

**Description**

A path component in the target path that must be a directory is not a directory.

**Possible Causes**

A path component in the target path is actually a regular file, causing path resolution to fail.

**Solution**

Check whether each path component in the target path is a directory (you can use the [statSync](js-apis-file-fs.md#fileiostatsync) API of [@ohos.file.fs](js-apis-file-fs.md) to determine whether a path component is a directory), correct the target path, and retry.

## 34400024 Target Path Does Not Exist

**Error Message**

A required file or directory does not exist while resolving or accessing the target path.

**Description**

The target path does not exist when accessing the resolved path.

**Possible Causes**

The target file or a path segment in its path has been deleted or moved.

**Solution**

Confirm that the target file exists and retry.

## 34400025 File Name or Path Too Long

**Error Message**

The file name or path is too long.

**Description**

The file name or path exceeds the maximum length allowed by the system.

**Possible Causes**

The passed file path or the file name contained in it exceeds the system limit.

**Solution**

A single file name can be up to 255 bytes, and a complete path can be up to 4096 bytes. Shorten the file name or path and retry.

## 34400029 Cloud Drive Application Rejects Dehydration

**Error Message**

The cloud disk provider did not approve the dehydration request.

**Description**

The third-party cloud drive application rejected the dehydration authorization.

**Possible Causes**

Before dehydration, the system sends a dehydration authorization request to the third-party cloud drive application. The cloud drive application returns that dehydration is not allowed (for example, the file is being used on the cloud side).

**Solution**

This error indicates that the third-party cloud drive application did not authorize this dehydration. The file remains unchanged, and no action is required.

## 34400031 Placeholder File Fully Hydrated

**Error Message**

The placeholder is already fully hydrated.

**Description**

The placeholder file is already fully hydrated, and no further hydration is required.

**Possible Causes**

Hydration is initiated again on a placeholder file that is already fully hydrated.

**Solution**

No action is required. Hydration is completed at the original path, and the file content is written to the filePath passed when calling [hydratePlaceholder](js-apis-file-clouddiskmanager-sys.md#hydrateplaceholder)(), which can be accessed directly.

## 34400032 No Hydration Task in Progress

**Error Message**

Cancellation was requested, but no hydrate task is pending or in progress.

**Description**

The target file has no hydration task in progress.

**Possible Causes**

When [hydratePlaceholder](js-apis-file-clouddiskmanager-sys.md#hydrateplaceholder)() is called to cancel hydration (with callbackType set to CANCEL_FETCH_DATA), the target file has no hydration task in progress.

**Solution**

No action is required.

## 34400033 Invalid Placeholder State

**Error Message**

The placeholder state or its stored attribute is invalid.

**Description**

The state or attribute stored in the placeholder file is invalid.

**Possible Causes**

The state value of the placeholder file is outside the valid range, or its recorded attribute information is corrupted.

**Solution**

Confirm that the placeholder file is created normally by the third-party cloud drive application and that its state value is within the valid range, and then retry. If this error persists, ask the third-party cloud drive application to recreate the placeholder file.

## 34400034 Active Hydration Task Limit Reached

**Error Message**

The limit on pending hydrate tasks has been reached.

**Description**

The number of pending (queued) hydration tasks has reached the limit.

**Possible Causes**

The number of pending hydration tasks for a single cloud drive application or globally has reached the system limit.

**Solution**

Wait for some hydration tasks to complete or be canceled before retrying. You can subscribe to hydration progress events through [onHydrateProgress](js-apis-file-clouddiskmanager-sys.md#onhydrateprogress)(), and initiate hydration again after receiving the COMPLETED or CANCELLED status.
