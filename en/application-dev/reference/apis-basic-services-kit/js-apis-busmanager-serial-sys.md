# @ohos.busManager.serial (Serial Port Management) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4f64ff5b14c025dff8030b4cb75d43326c949fa0 translatedAt=2026-09-01T03:36:16.774Z pushedAt=2026-09-01T08:52:26.440Z -->

This module provides an API for serial port management, including obtaining the serial port list, enabling and disabling a serial port, reading and writing data, hardware-based flow control for signal management, and authorization. This module is applicable to scenarios where serial port communication with external devices is required, such as embedded device control and industrial data collection. It provides stable and efficient hardware communication capabilities.

**Since:** 26.0.0

## Modules to Import

```ts
import { serial } from '@kit.BasicServicesKit';
```

## serial.addPortAuthorization

addPortAuthorization(tokenId: string, deviceId: string): Promise&lt;void&gt;

Adds the authorization for the app to access the serial port. This function associates the token ID of an app with the ID of a serial port device to enable the app to access the serial port. This function can be used by a system management app to grant serial port access permission to a third-party app. For example, a device management tool can use this function to grant serial port access permission to an industrial data collection app. This function is available only to system apps that display a dialog box for serial port authorization. After the user grants the permission, the permission information is persistently stored. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**System capability:** SystemCapability.BusManager.Serial

**Parameters:**

| Name    | Type    | Mandatory| Description                                                        |
| --------- | -------- | ---- | ------------------------------------------------------------ |
| tokenId   | string   | Required   | Token ID of the authorized app, which identifies the app that is granted the permission to access the serial port. After the setting, the app is granted the permission to access the specified serial port device. It can be obtained using [bundleManager.getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself).|
| deviceId  | string   | Required   | ID of the serial port device, which specifies the serial port device to be accessed. You can obtain the serial port list using [getSerialPortList](./js-apis-busmanager-serial.md#serialgetserialportlist). For an onboard serial port, the value is the port name. For a USB virtual serial port, the value is the combination of VID+PID+SN or the device path (for example, **/dev/ttyUSB0**). After the setting, the app will obtain the access permission for the specified serial port device. |

**Return value**

| Type               | Description                   |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [Serial Port Management Error Codes](errorcode-busmanager-serial.md).

| ID| Error Message                                         |
| -------- | ------------------------------------------------- |
| 202      | Permission denied. Called by non-system application. |
| 35700001 | Service error.                                    |
| 35700002 | Invalid parameter.                                |
| 35700008 | Permission denied.                                |

**Example**

```ts
import {BusinessError} from '@kit.BasicServicesKit';
// Add the serial port access permission.
// The token ID needs to be obtained using the bundleManager.getBundleInfoForSelf API. The value here is only an example.
let tokenId: string = '123456';
let deviceId: string = '/dev/ttyUSB0';
serial.addPortAuthorization(tokenId, deviceId).then(() => {
  console.info('addPortAuthorization success');
}).catch((error: BusinessError) => {
  console.error(`Failed to addPortAuthorization. Code: ${error.code}, message: ${error.message}`);
});
```
