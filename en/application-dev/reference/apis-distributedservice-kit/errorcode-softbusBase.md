# Device Awareness Error Codes
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=c951a8e46e7eaf0320cd680d744c662db4826584 translatedAt=2026-11-04T05:23:29.070Z pushedAt=2026-11-04T10:12:33.556Z nl=1 -->

The device perception module provides device discovery and perception capabilities based on the distributed soft bus. It supports scanning nearby devices and obtaining the list of perceived devices, and is applicable to scenarios such as device interconnection and distributed services that require discovering nearby devices.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2000001 Internal Error

**Error Message**

Internal error.

**Description**

An internal error occurs, and the system encounters an unexpected error, causing the request to fail.

**Possible Causes**

An internal system error occurs, such as a distributed soft bus service exception or a memory allocation failure.

**Solution**

Verify that the distributed soft bus service is running properly, and then retry. If the failure persists, restart the device or capture hilog logs for feedback.

## 2000002 Calling Sequence Error

**Error Message**

Caller error.

**Description**

The caller failed to call the APIs in the specified sequence, and the request failed.

**Possible Causes**

The caller did not call [startPerceptionScan](js-apis-softbusBase-sys.md#softbusbasestartperceptionscan) to start scanning first, or called [getPerceptionDeviceList](js-apis-softbusBase-sys.md#softbusbasegetperceptiondevicelist) to obtain the device list after calling [stopPerceptionScan](js-apis-softbusBase-sys.md#softbusbasestopperceptionscan) to stop scanning.

**Solution**

Call startPerceptionScan to start scanning first, and then call getPerceptionDeviceList to obtain the device list. Do not query the device list after stopping scanning.

## 2000003 Temporary Error

**Error Message**

Temporary error.

**Description**

A temporary error. The request failed due to a temporary cause and can be retried.

**Possible Causes**

Temporary errors such as busy system resources or transient unavailability of the underlying layer.

**Solution**

It is recommended that you retry the API call after waiting for 3 to 5 seconds. If the failure persists, capture the hilog log and provide feedback.

## 2006001 Underlying Module Error

**Error Message**

Underlying module error.

**Description**

The underlying module error occurs when the request fails due to an exception in another underlying module. Retry after an interval of 30 seconds.

**Possible Causes**

An error occurs in a dependent underlying module (such as Bluetooth or transport).

**Solution**

Retry after an interval of 30 seconds. If the failure persists, check whether the underlying module (such as Bluetooth) is enabled properly, and capture the hilog log for feedback.
<!--no_check-->