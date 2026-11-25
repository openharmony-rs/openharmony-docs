# Input Device Error Codes

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=615911b0ee49fce00580141968cadc359896d5c7 translatedAt=2026-11-04T04:33:30.636Z pushedAt=2026-11-04T08:04:44.680Z nl=1 -->

> **NOTE**
>
> - This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

<!--Del-->
## 3900001 Device Not Exist

**Error Message**

The specified device does not exist.

**Description**

This error code is reported if the specified device cannot be found in the multimodal device list.

**Possible Causes**

1. The ID of the input device has changed.
2. The physical connection of the input device is disconnected.

**Procedure**

1. Use [inputDevice.getDeviceList](js-apis-inputdevice.md#inputdevicegetdevicelist9) to query the device ID, and then pass in the correct device ID.
2. Check whether the keyboard cable is disconnected.<!--DelEnd-->

## 3900002 Keyboard Not Connected

**Error Message**

There is currently no keyboard device connected.

**Description**

This error code is reported if no connected keyboard is detected.

**Possible Causes**

The physical connection of the input device is disconnected.

**Procedure**

Check whether the keyboard cable is disconnected.

## 3900003 API Call Failed for a Non-Input Application

**Error Message**

It is prohibited for non-input applications.

**Description**

This error code is reported if the API is called by a non-input application.

**Possible Causes**

Non-input applications call this API.

**Procedure**

Use an input application to call this API.

<!--Del-->
## 3900004 The Specified Display Does Not Exist

**Error Message**

The specified display does not exist.

**Description**

The specified displayId does not exist.

**Possible Causes**

The current device does not have this display ID.

**Solution**

1. Query the valid display ID and pass in the correct display ID.
2. Check the connection status of the display.<!--DelEnd-->

<!--Del-->
## 3900005 Unsupported input device

**Error Message**

Unsupported input device.

**Description**

This peripheral device is not supported.

**Possible Causes**

The peripheral device corresponding to the specified inputDeviceId is not an external USB or Bluetooth peripheral device.

**Solution**

Set the ID of the external USB or Bluetooth peripheral device again.<!--DelEnd-->

## 3800001 Multimodal input internal error

**Error Message**

Input service exception. Possible causes: 1. Memory allocation failure. 2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later.

**Description**

Internal error of the multimodal input service.

**Possible Causes**

Unexpected errors occurred, such as memory allocation failure, busy thread, and service execution.

**Procedure**

Try again later.