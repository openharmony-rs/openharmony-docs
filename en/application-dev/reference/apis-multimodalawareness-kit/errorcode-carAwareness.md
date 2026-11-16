# Car Awareness Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=481a92d618b9d348ab029a2e191d34bca2a18623 translatedAt=2026-11-04T06:09:50.385Z pushedAt=2026-11-04T08:04:44.812Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 34000001 Service Exception

**Error Message**

Service exception.

**Description**

This error code is reported when a service exception occurs while calling the onSpatialMotion, offSpatialMotion, onRealTimeWeather, offRealTimeWeather, onRefueling, offRefueling, and getAllCapabilityList APIs of the carAwareness module.

**Possible Causes**

The service status is abnormal.

**Solution**

1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the service remains unavailable after three consecutive retries, stop attempting and prioritize obtaining device logs for further analysis.

## 34000002 Specific Capability Not Supported

**Error Message**

Specific capability not supported.

**Description**

This error code is reported when the specified capability is not supported while calling the onSpatialMotion, onRealTimeWeather, or onRefueling API of the carAwareness module.

**Possible Causes**

1. The device hardware does not have the sensors required by the corresponding awareness capability (such as an exterior camera or rear-seat camera).
2. The current device model is not adapted to this awareness capability and is not in the capability support list.
3. The passed awareness capability parameter is invalid and is not within the valid value range of the Capability enum.

**Solution**

1. Call the `getAllCapabilityList` API in advance to query the awareness capability list supported by the current device, and confirm that the capability to be used is within the supported range before calling the corresponding API.
2. Check whether the passed Capability parameter is a valid enum value to avoid spelling errors or passing undefined values.
3. For devices that do not support this capability, implement degraded adaptation in the service to avoid directly calling the corresponding API and triggering an exception.

