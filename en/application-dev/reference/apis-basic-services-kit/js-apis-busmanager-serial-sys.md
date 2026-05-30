# @ohos.busManager.serial (Serial Port Management) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

This module provides an API for serial port management, including obtaining the serial port list, enabling and disabling a serial port, reading and writing data, hardware-based flow control for signal management, and authorization.

**Since:** 26.0.0

## Modules to Import

```ts
import { serial } from '@kit.BasicServicesKit';
```

## serial.addPortAuthorization

addPortAuthorization(tokenId: string, deviceId: string): Promise&lt;void&gt;

Adds the authorization for the application to access the serial port. This API is available only to system applications that display a pop-up window for serial port authorization. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name    | Type    | Mandatory| Description                                                        |
| --------- | -------- | ---- | ------------------------------------------------------------ |
| tokenId   | string   | Yes  | Token ID of the authorized application.                                      |
| deviceId  | string   | Yes  | ID of the serial port device. For an onboard serial port, the value is the port name. For a USB virtual serial port, the value is the combination of VID+PID+SN.|

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| Error Code| Error Message                                         |
| -------- | ------------------------------------------------- |
| 202      | Permission denied. Called by non-system application. |
| 35700001 | Service error.                                    |
| 35700002 | Invalid parameter.                                |
| 35700008 | Permission denied.                                |

**Example**

```ts
import { serial } from "@kit.BasicServicesKit";

// Add the serial port access permission (available only to system applications).
let tokenId: string = '123456';
let deviceId: string = '/dev/ttyUSB0';
serial.addPortAuthorization(tokenId, deviceId).then(() => {
  console.info('addPortAuthorization success');
}).catch((error: Error) => {
  console.error(`addPortAuthorization error: ${JSON.stringify(error)}`);
});
```
