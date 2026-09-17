# addAccessoryRight (System API)

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## addAccessoryRight

```TypeScript
function addAccessoryRight(tokenId: number, accessory: USBAccessory): void
```

Adds the permission to apps for accessing USB accessories. This API can be used by system apps to grant third-party apps the permission to access USB accessories. **usbManager.requestAccessoryRight** triggers a dialog box to request user authorization. **addAccessoryRight** does not trigger a dialog box but directly adds the device accessory access permission for the app. The authorization takes effect immediately and is stored persistently. It remains valid even after the device is rebooted. The authorization applies to the specified USB device accessory instance. Multiple apps can obtain the access permission for the same accessory at the same time. Unlike **requestAccessoryRight**, **addAccessoryRight** does not require user interaction and is suitable for scenarios where the system app automatically grants authorization.

> **NOTE:** 
> 
> This API is supported since API version 14.

**Since:** 14

**Required permissions:** ohos.permission.MANAGE_USB_CONFIG

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenId | number | Yes | Unique ID of an app, which can be obtained using [bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md). |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | Yes | USB accessory object, including the accessory ID and attributes. You can obtain the accessory list by calling [getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md). For details about the field definition, see [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The permission check failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Normal application do not have permission to use system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| [14400004](../errorcode-usb.md#14400004-service-exception) | Service exception. Possible causes:<br>1. No accessory is plugged in. |
| [14400005](../errorcode-usb.md#14400005-database-operation-exception) | Database operation exception. |
