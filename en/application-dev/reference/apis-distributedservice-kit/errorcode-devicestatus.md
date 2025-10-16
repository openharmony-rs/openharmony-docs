# Device Status Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 32500001 Abnormal Service

**Error Message**

Service exception.

**Symptom**

This error code is reported if a service exception occurs when the **on** or **off** API of the deviceStatus module is called.

**Possible Causes**

The service status is abnormal.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. During this period, you can preferentially obtain the device list to check for device availability.

## 32500002 Subscription Failed

**Error Message**

Subscription failed.

**Symptom**

This error code is reported if subscription fails when the **on** API of the deviceStatus module is called.

**Possible Causes**

Subscription to change events has failed.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 

## 32500003 Unsubscription Failed

**Error Message**

Unsubscription failed.

**Symptom**

This error code is reported if unsubscription fails when the **off** API of the deviceStatus module is called.

**Possible Causes**

Unsubscription from change events has failed.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 
