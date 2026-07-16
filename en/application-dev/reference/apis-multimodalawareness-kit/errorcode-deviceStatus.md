# Device Status Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=d18790e6ef1247c1fd8194f3838e7698bf6e9bf2 translatedAt=2026-06-24T06:29:28.421Z pushedAt=2026-06-25T01:35:11.423Z -->

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
2. If the operation fails for three consecutive times, stop the retry. You can also attempt to obtain the sensor list to check for device availability.

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