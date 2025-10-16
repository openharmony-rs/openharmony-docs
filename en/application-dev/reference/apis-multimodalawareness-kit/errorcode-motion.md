# Motion Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 31500001 Service Exception

**Error Message**

Service exception. Possible causes: 1. A system error, such as null pointer, container-related exception; 2. N-API invocation exception, invalid N-API status.

**Symptom**

This error code is reported if a service exception occurs when the **on**, **off**, or **get** API of the motion module is called.

**Possible Causes**

The service status is abnormal.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. You can also attempt to obtain the sensor list to check for device availability.



## 31500002 Subscription Failed

**Error Message**

Subscription failed. Possible causes: 1. Callback registration failure; 2. Failed to bind native object to js wrapper; 3. N-API invocation exception, invalid N-API status; 4. IPC request exception.

**Symptom**

This error code is reported if subscription fails when the **on** API of the motion module is called.

**Possible Causes**

Subscription to change events has failed.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 



## 31500003 Unsubscription Failed

**Error Message**

Unsubscription failed. Possible causes: 1. Callback failure; 2. N-API invocation exception, invalid N-API status; 3. IPC request exception.

**Symptom**

This error code is reported if unsubscription fails when the **off** API of the motion module is called.

**Possible Causes**

Unsubscription from change events has failed.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 
