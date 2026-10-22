# workScheduler Error Codes

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d5faa0a49f7aa05b46e226421c5d5fb30796f2fe translatedAt=2026-09-15T12:49:02.061Z pushedAt=2026-09-17T09:32:27.635Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 9700001 Memory Operation Failure

**Error Message**

Memory operation failed.

**Description**

Memory operation failed.

**Possible Causes**

1. A memory leak occurs.
2. The system memory is insufficient.

**Solution**

1. Check for memory leak in the app code, such as unreleased objects and circular references.
2. Check the memory usage of the app and release unnecessary memory resources.

## 9700002 Parcel Read/Write Operation Failure

**Error Message**

Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory.

**Description**

This error code is reported when parcel data fails to be read or written during IPC.

**Possible Causes**

1. The data object fails to be read or written during IPC.
2. The memory fails to be allocated for the read or write operation.

**Solution**

The system is experiencing an internal error. Try again later or restart the device.

## 9700003 System Service Failure

**Error Message**

System service operation failed.

**Description**

The client process fails to request the system service.

**Possible Causes**

1. The system service is not started.
2. The system service is abnormal.

**Solution**

The system service is experiencing an internal error. Try again later or restart the device.

## 9700004 Parameter Verification Failed

**Error Message**

Input param failed.

**Description**

Invalid input parameter.

**Possible Causes**

1. For parameter **workInfo**, the bundle name does not match the app UID.
2. The Work Scheduler task to cancel or query does not exist.
3. For parameter **taskInfo**, the ability name is not a launcher ability or the task ID verification fails.

**Solution**

1. Check whether the bundle name in **workInfo** matches the app UID.
2. If this error occurs when you cancel or query a deferred task, ensure that the task has been correctly created.
3. Check whether the ability name in **taskInfo** is a launcher ability.
4. If you want to complete, query, or cancel a registered update task in the background, check whether the task ID is correct.

## 9700005 StartWork Failure

**Error Message**

Calling startWork failed.

**Description**

This error code is reported when the request for a deferred task fails.

**Possible Causes**

1. The deferred task already exists.
2. Each application UID can add up to 10 delayed tasks.
3. The repeat interval of a Work Scheduler task must be at least 20 minutes.

**Solution**

1. If a message is displayed indicating that the task already exists, do not create the same task again.
2. Check whether the app has requested more than 10 deferred tasks.
3. Check whether the repeat interval of the duplicate task is at least 20 minutes.
<!--Del-->
## 9700006 Failed to Verify the Execution Frequency Parameters

**Error Message**

Failed to check the execution frequency parameters.

**Description**

Failed to check the execution frequency parameters.

**Possible Causes**

1. The **uid** parameter does not exist or is in an incorrect format.
2. The **workId** parameter is in an incorrect format or does not exist.
3. The **interval** parameter is in an incorrect format or is not within the allowed range.

**Solution**

1. Check whether the **uid** parameter matches the app UID.
2. Check whether the **workId** parameter matches the work ID of the deferred task requested by the app.
3. Check whether the **interval** parameter is within the allowed range.
<!--DelEnd-->
