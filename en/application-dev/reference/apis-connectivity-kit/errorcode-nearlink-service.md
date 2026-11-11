# NearLink Error Codes
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=304517cf5105092ff7ebb1be0da01c6a3f1d16fb translatedAt=2026-11-10T05:00:48.320Z pushedAt=2026-11-10T07:21:54.879Z nl=1 -->


> **NOTE**
> 
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).


## 36100003 NearLink Disabled

**Error Message**

NearLink disabled.

**Description**

This error code is returned if a relevant API is called when NearLink is off.

**Possible Causes**

NearLink is turned off.

**Solution**

On the settings screen of the device, turn on NearLink and try again (the typical path is **Settings** &gt; **NearLink &amp; Bluetooth** &gt; **NearLink**, or **Settings** &gt; **More connectivity options** &gt; **NearLink** for different products or system versions). Alternatively, submit an issue via [Online Ticket](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100020 Duplicate Port Registration

**Error Message**

The UUID is already registered.

**Description**

A port with the UUID has been registered.

**Possible Causes**

The same UUID is used to create a port repeatedly.

**Solution**

Call the [dataTransfer.destroyPort](js-apis-nearlink-data-transfer-api.md#datatransferdestroyport) API to destroy the port with the UUID, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100021 Number of Registered Ports Exceeds the Upper Limit

**Error Message**

Port exceeds the upper limit.

**Description**

The number of registered ports exceeds the upper limit.

**Possible Causes**

The number of ports allocated for data transfer reaches the upper limit.

**Solution**

Call [dataTransfer.destroyPort](js-apis-nearlink-data-transfer-api.md#datatransferdestroyport) to destroy other registered ports, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100022 Port Not Registered

**Error Message**

The UUID is not registered.

**Description**

No port with the UUID is registered.

**Possible Causes**

An attempt is made to destroy an unregistered port.

**Solution**

Ensure that the port to be destroyed has been registered, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100023 Data Transmission Congestion

**Error Message**

Write data congestion.

**Description**

Data transmission fails due to congestion.

**Possible Causes**

Data transmission in reliable transmission mode fails due to congestion at the protocol layer or on the chip.

**Solution**

Control data write traffic, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100040 Integer Out of Range

**Error Message**

Integer out of range.

**Description**

The integer is out of range.

**Possible Causes**

The input integer parameter is out of the value range defined by the API.

**Solution**

Change the integer parameter value to a valid value within the range defined by the API (for details about the value range, see the parameter description of the corresponding API). Alternatively, submit an issue via [Online Ticket](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100041 Invalid URL

**Error Message**

Invalid address.

**Description**

The URL is invalid.

**Possible Causes**

The input address parameter is in an incorrect format, for example, the length does not meet the requirement or the parameter contains invalid characters.

**Solution**

Change the URL to a correct format, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).

A correct URL is in the format similar to **11:22:33:AA:BB:FF**, which consists of 17 characters, including hexadecimal digits and colons (:).


## 36100042 Empty Array

**Error Message**

Empty array.

**Description**

The array is empty.

**Possible Causes**

The input array parameter is empty, or the array does not contain valid elements.

**Solution**

Fill in the array correctly, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100043 Invalid UUID

**Error Message**

Invalid UUID.

**Description**

The UUID is invalid.

**Possible Causes**

The input UUID parameter is in an incorrect format, for example, the length does not meet the requirement or the parameter contains invalid characters.

**Solution**

Change the UUID to a correct format, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).

A correct UUID is in the format similar to **FFFFFFFF-1234-5678-ABCD-000000001234**, which consists of 36 characters, including hexadecimal digits and hyphens (-), representing a 128-bit ID.


## 36100044 Standard NearLink Service UUID Not Allowed

**Error Message**

NearLink standard UUID not allowed.

**Description**

The standard NearLink service UUID is not allowed.

**Possible Causes**

The NearLink standard service UUID is not allowed in the API parameters. It is not allowed in the following scenarios:

1. The NearLink standard service UUID cannot be directly passed as a parameter.

2. The NearLink standard service UUID cannot be included in service structures such as custom services, attributes, and methods.

**Solution**

Replace the standard service UUID in the API parameters with a custom service UUID, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).

A standard service UUID is formed by concatenating the first 112 bits of the Base UUID (37BEA880-FC70-11EA-B720-000000000000), which is officially defined by the SparkLink Alliance, with a 16-bit standard identifier. A custom service UUID must not use the first 112 bits of the Base UUID as its prefix.


## 36100050 Coordinated Device Set Management Not Supported

**Error Message**

Coordinated Devices Set Management not supported.

**Description**

The device does not support coordinated device set management.

**Possible Causes**

The current device hardware does not support the coordinated device set management function.

**Solution**

To use the coordinated device set management function, use a device that supports the NearLink coordinated device set management feature, such as the phones and tablets that support NearLink audio. You can also query the device capability API to check whether the device supports this feature, or [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).


## 36100099 Operation Failed

**Error Message**

Operation failed.

**Description**

An unexpected internal error occurred during system processing.

**Possible Causes**

An unknown error occurred.

If the device has been paired, this error code will be returned when you call [startPairing](js-apis-nearlink-remote-device.md#startpairing) to initiate pairing.

**Solution**

Try again. If the problem persists, [submit a ticket online](https://developer.huawei.com/consumer/en/support/feedback/#/).
