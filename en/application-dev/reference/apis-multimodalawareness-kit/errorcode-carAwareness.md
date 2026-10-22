# Car Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=561a48f0279b682322ad16aa122a3161b679e716 translatedAt=2026-09-14T01:39:30.817Z pushedAt=2026-09-14T10:03:33.565Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34000001 Service Exception

**Error Message**

Service exception.

**Description**

This error code is reported if a service exception occurs when the **onSpatialMotion**, **offSpatialMotion**, **onRealTimeWeather**, **offRealTimeWeather**, **onRefueling**, **offRefueling**, and **getAllCapabilityList** APIs of the **carAwareness** module are called.

**Possible Causes**

The service status is abnormal.

**Solution**

1. Retry the operation at regular intervals, for example, at an interval of 1s or at exponentially increasing intervals.
2. Stop retrying if the operation remains unavailable after three consecutive attempts. During this period, obtain the device logs first for further analysis.

## 34000002 Specified Capability Not Supported

**Error Message**

Specific capability not supported.

**Description**

This error code is reported when the specified capability is not supported while calling the **onSpatialMotion**, **onRealTimeWeather**, or **onRefueling** API of the **carAwareness** module.

**Possible Causes**

1. The device hardware does not have the sensors required for the corresponding awareness capability (such as an exterior camera or rear-seat camera).
2. The current device model is not adapted to this awareness capability and is not in the supported capability list.
3. The passed awareness capability parameter is invalid and is not within the valid value range of the **Capability** enum.

**Solution**

1. Call the `getAllCapabilityList` API in advance to query the awareness capability list supported by the current device, and confirm that the capability to be used is within the supported range before calling the corresponding API.
2. Check whether the passed Capability parameter is a valid enum value to avoid spelling errors or passing undefined values.
3. For devices that do not support this capability, implement degradation adaptation in the service to avoid directly calling the corresponding API and triggering an exception.

