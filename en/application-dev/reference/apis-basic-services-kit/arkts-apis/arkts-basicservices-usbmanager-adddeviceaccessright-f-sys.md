# addDeviceAccessRight (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## addDeviceAccessRight

```TypeScript
function addDeviceAccessRight(tokenId: string, deviceName: string): boolean
```

Adds the authorization for the app to access the device. System applications are granted the device access permission by default, and calling this API will not revoke the permission. This API can be used by system settings apps or device management apps to grant third-party apps the permission to access USB devices. The authorization takes effect immediately and is stored persistently. It remains valid even after the device is rebooted. The authorization applies to the specified USB device instance. Multiple apps can obtain the access permission for the same device at the same time.

[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md) triggers a dialog box to request user authorization. **addDeviceAccessRight** does not trigger a dialog box but directly adds the device access permission for the app.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenId | string | Yes | Unique ID of an app, which can be obtained using [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md). |
| deviceName | string | Yes | Device name, in the format of **bus-port**, for example, **1-1**. The value can be found in the device list obtained using the [getDevices](arkts-basicservices-usbmanager-getdevices-f.md) API. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Permission addition result. The value **true** indicates that the access permission is added successfully; and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 18 and later |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
