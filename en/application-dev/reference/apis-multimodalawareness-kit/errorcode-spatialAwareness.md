# Spatial Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

> **Notes**:
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 35100001 Service Exception

**Error Message**

Service exception.

**Description**

This error code is reported if a service exception occurs when the onDistanceMeasure, onIndoorOrOutdoorIdentify, offDistanceMeasure, or offIndoorOrOutdoorIdentify API of the distanceMeasurement module is called.

**Possible Causes**

The service status is abnormal.

**Procedure**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. During this period, you can preferentially obtain the device list to check for device availability.



## 35100002 Subscription Failed

**Error Message**

Subscription failed.

**Description**

This error code is reported if the subscription fails when the onDistanceMeasure or onIndoorOrOutdoorIdentify API of the distanceMeasurement module is called.

**Possible Causes**

Subscription error.

**Procedure**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 



## 35100003 Unsubscription Failed

**Error Message**

Unsubscription failed.

**Description**

This error code is reported if the unsubscription fails when the offDistanceMeasure or offIndoorOrOutdoorIdentify API of the distanceMeasurement module is called.

**Possible Causes**

Unsubscription from status change events has failed.

**Procedure**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 



## 35100004 Invalid Parameter

**Error Message**

Parameter invalid.

**Description**

This error code is reported when the distance measurement API of the distanceMeasurement module is called but the parameter value is out of range.

**Possible Causes**

The parameter value is out of range.

**Procedure**

1. Enter correct parameters by referring to the API document.
