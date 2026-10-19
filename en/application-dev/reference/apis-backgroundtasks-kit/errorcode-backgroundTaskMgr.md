# backgroundTaskManager Error Codes

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=6da3a7aa405098fd3e112d6253fc2fa6f4b15670 translatedAt=2026-09-15T12:48:35.344Z pushedAt=2026-09-17T03:16:07.745Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 9800001 Memory Operation Failure

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

## 9800002 Parcel Read/Write Operation Failure

**Error Message**

Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory.

**Description**

When an API related to a continuous task is called, the read or write operation fails during IPC.

**Possible Causes**

1. The data object fails to be read or written during IPC.
2. The memory fails to be allocated for the read or write operation.

   During RPC, the sender can use the **write()** method provided by **MessageParcel** to write the data to be sent in a specific format to the object. The receiver can use the **read()** method provided by **MessageParcel** to read data in a specific format from the object.

**Solution**

The system is experiencing an internal error. Try again later or restart the device.

## 9800003 IPC Failure

**Error Message**

Internal transaction failed.

**Description**

Failed to conduct inter-process communication.

**Possible Causes**

IPC fails.

**Solution**

The system is experiencing an internal error. Try again later or restart the device.

## 9800004 System Service Failure

**Error Message**

System service operation failed.

**Error Description**

When an API related to a continuous task is called, the client process fails to request the system service.

**Possible Causes**

1. The system service is not started.
2. The system service is abnormal.

**Handling Procedure**

The system service is experiencing an internal error. Try again later or restart the device.

## 9800005 Long-Running Task Verification Failure

**Error Message**

Continuous task verification failed.

**Description**

This error code is reported when continuous task verification fails.

**Possible Causes**

1. The application repeatedly requests a Long-Running Task.
2. The application repeatedly cancels a Long-Running Task.
3. The value of **bgMode** is invalid because no Long-Running Task type is configured for **backgroundModes** in the application's configuration file.
4. In API version 20 and earlier versions, only PCs and 2-in-1 devices can request a continuous task using [TASK_KEEPING](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundmode).
5. The main type or subtype of the Long-Running Task is not configured.
6. The main type and subtype of the Long-Running Task have inconsistent lengths or mismatched types.
7. The main type or subtype of the continuous task is not defined.
8. The input **continuousTaskId** is invalid.
9. The data transmission type does not support notification combination.
10. The Long-Running Task notification does not exist and cannot be combined.
11. Neither the current Long-Running Task nor the target Long-Running Task supports notification combination.
12. The Long-Running Task types of the combined notifications are inconsistent.
13. The app has not obtained ACL authorization when requesting a [TASK_KEEPING](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundmode) continuous task.
14. The data transmission type does not support updating the continuous task type via the update API.
15. A new Long-Running Task Type (other than audio playback) is requested in the background.
16. The application has not obtained ACL authorization when requesting a continuous task of the [MODE_SPECIAL_SCENARIO_PROCESSING](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmode21) type.

**Solution**

1. Check the application code.
2. Check whether the application has the system permissions.
3. Check the value of **backgroundModes**.
4. Check the type of the device where the app is located.
5. Check whether the main type and subtype of the Long-Running Task are configured.
6. Check whether the main type and subtype of the continuous task are of the same length or whether their types match.
7. Check whether the main type and subtype of the continuous task are out of range.
8. Check whether the input **continuousTaskId** parameter is valid.
9. During notification combination, check whether the requested continuous task type includes the data transmission type.
10. During notification combination, check whether the Long-Running Task notification exists.
11. During notification combination, confirm whether the current Long-Running Task or the target Long-Running Task supports notification combination.
12. During notification combination, check whether the continuous task types are consistent.
13. Check whether the app has obtained the [ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system) ACL authorization when requesting a continuous task of the [TASK_KEEPING](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundmode) type.
14. When updating the continuous task, check whether either the original type or the new type includes the data transmission type.
15. Check if any other Long-Running Task types are being requested in the background, other than audio playback and Long-Running Task types that have already been requested in the foreground.
16. Check whether the application has obtained the [ohos.permission.KEEP_BACKGROUND_RUNNING_SPECIAL_SCENARIO](../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_special_scenario) or [ohos.permission.KEEP_BACKGROUND_RUNNING_SYSTEM](../../security/AccessToken/restricted-permissions.md#ohospermissionkeep_background_running_system) ACL authorization when requesting a continuous task of the [MODE_SPECIAL_SCENARIO_PROCESSING](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmode21) type.

## 9800006 Notification Verification Failure for a Long-Running Task

**Error Message**

Notification verification failed for a continuous task.

**Description**

This error code is reported when notification verification in a Long-Running Task fails.

**Possible Causes**

1. The Long-Running Task resources cached in the resource subsystem fail to be loaded.
2. The notification subsystem functions abnormally.
3. When the continuous-task notification is updated, the continuous task ID and notification progress are incorrect.
4. When the continuous-task notification is updated, the continuous task does not contain the data transfer type.

**Solution**

1. Check whether the Long-Running Task resource **ohos.backgroundtaskmgr.resources** exists.
2. The system service is experiencing an internal error. Try again later or restart the device.
3. Check whether the continuous task ID and notification progress are correct when the continuous-task notification is updated. If not, pass the correct parameters.
4. Check whether the continuous task contains the data transfer type when the continuous-task notification is updated. If not, request or update the continuous task again.

## 9800007 Long-Running Task Storage Failure

**Error Message**

Continuous task storage failed.

**Description**

This error code is reported when information storage in a continuous task fails. 

**Possible Causes**

1. Failed to create a file to store the task information.
2. Failed to obtain the real file path.
3. Failed to open the file that stores the task information.

**Solution**

1. Check the **/data/service/el1/public/background_task_mgr/running_task** file.
2. The system is experiencing an internal error. Try again later or restart the device.

## 9900001 Caller Information Verification Failure for a Transient Task

**Error Message**

Caller information verification failed for a transient task.

**Description**

This error code is reported when caller information verification in a transient task fails.

**Possible Causes**

1. The UID or PID of the caller fails to be obtained. As a result, the verification fails.
2. The bundle name of the caller fails to be obtained. As a result, the verification fails.
3. The request ID passed in the API used to cancel the transient task is invalid.

**Solution**

1. Check whether the application UID exists.
2. Check whether the application has requested a transient task.
3. The system service is experiencing an internal error. Try again later or restart the device.

## 9900002 Transient Task Verification Failure

**Error Message**

Transient task verification failed.

**Description**

This error code is reported when transient task verification fails.

**Possible Causes**

1. The callback passed in [requestSuspendDelay](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerrequestsuspenddelay) already exists.
2. The callback passed in [cancelSuspendDelay](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagercancelsuspenddelay) does not exist.
3. The app attempts to request a transient task 5 seconds after it switches to the background. If the request is made after this period, the verification will fail.
4. An application cannot request more than three transient tasks.
5. The application's remaining daily quota for transient tasks is insufficient.

**Solution**

1. Check whether an existing callback object is passed when [requestSuspendDelay](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerrequestsuspenddelay) is called.
2. Check whether a nonexistent callback object is passed when [cancelSuspendDelay](./js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagercancelsuspenddelay) is called.
3. Check whether the app has requested a transient task 5 seconds after it is moved to the background.
4. Check whether the app has requested more than three transient tasks.
5. Check whether the remaining daily quota of transient tasks for the app is sufficient.

## 9900003 Parcel Read/Write Operation Failure

**Error Message**

Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory.

**Description**

When an API related to a transient task is called, the read or write operation fails during IPC.

**Possible Causes**

1. The data object fails to be read or written during IPC.
2. The memory fails to be allocated for the read or write operation.

   During RPC, the sender can use the **write()** method provided by **MessageParcel** to write data in a specific format to the MessageParcel object. The receiver can use the **read()** method provided by **MessageParcel** to read data in a specific format from the MessageParcel object.

**Handling Procedure**

The system is experiencing an internal error. Try again later or restart the device.

## 9900004 System Service Failure

**Error Message**

System service operation failed.

**Description**

When an API related to a transient task is called, the client process fails to request the system service.

**Possible Causes**

1. The system service has not started yet.
2. The system service is abnormal.

**Solution**

The system service is experiencing an internal error. Try again later or restart the device.
<!--Del-->
## 18700001 Caller Information Verification Failure for an Energy Resource Request

**Error Message**

Caller information verification failed for an energy resource request.

**Description**

This error code is reported when caller information verification in an energy resource request fails.

**Possible Causes**

1. Failed to obtain the UID or PID of the caller.
2. The resourceTypes for requesting resources exceeds the upper limit.

**Solution**

1. Check whether the UID or PID of the app is correct.
2. Check whether the value of **resourceTypes** for requesting resources exceeds the upper limit.

## 18700002 Parcel Read/Write Operation Failure

**Error Message**

Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory.

**Description**

When an API related to efficiency resources is called, the read or write operation fails during IPC.

**Possible Causes**

1. The data object fails to be read or written during IPC.
2. The memory fails to be allocated for the read or write operation.

   During RPC, the sender can use the write method provided by **MessageParcel** to write the data to be sent in a specific format to the object. The receiver can use the read method provided by **MessageParcel** to read data in specific format from a **MessageParcel** object.

**Solution**

The system is experiencing an internal error. Try again later or restart the device.

## 18700004 System Service Failure

**Error Message**

System service operation failed.

**Description**

When an API related to efficiency resources is called, the client process requests the efficiency resource system service process, and the request for the system service operation fails.

**Possible Causes**

1. The system service is not started.
2. The system service is abnormal.

**Solution**

The system service is experiencing an internal error. Try again later or restart the device.
<!--DelEnd-->