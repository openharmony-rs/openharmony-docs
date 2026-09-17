# addPortAuthorization (System API)

## Modules to Import

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## addPortAuthorization

```TypeScript
function addPortAuthorization(tokenId: string, deviceId: string): Promise<void>
```

Adds the authorization for the app to access the serial port. This function associates the token ID of an app with the ID of a serial port device to enable the app to access the serial port. This function can be used by a system management app to grant serial port access permission to a third-party app. For example, a device management tool can use this function to grant serial port access permission to an industrial data collection app. This function is available only to system apps that display a dialog box for serial port authorization. After the user grants the permission, the permission information is persistently stored. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BusManager.Serial

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenId | string | Yes | Token ID of the authorized app, which identifies the app that is granted the permission to access the serial port. After the setting, the app is granted the permission to access the specified serial port device. It can be obtained using [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md). |
| deviceId | string | Yes | ID of the serial port device, which specifies the serial port device to be accessed. You can obtain the serial port list using [getSerialPortList](arkts-basicservices-serial-getserialportlist-f.md). For an onboard serial port, the value is the port name. For a USB virtual serial port, the value is the combination of VID+PID+SN or the device path (for example, /dev/ttyUSB0). After the setting, the app will obtain the access permission for the specified serial port device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Called by non-system application |
| [35700001](../errorcode-busmanager-serial.md#35700001-abnormal-service) | Service error. |
| [35700002](../errorcode-busmanager-serial.md#35700002-parameter-error) | Invalid parameter. |
| [35700008](../errorcode-busmanager-serial.md#35700008-permission-denied) | Permission denied. |

**Examples**

```TypeScript
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
