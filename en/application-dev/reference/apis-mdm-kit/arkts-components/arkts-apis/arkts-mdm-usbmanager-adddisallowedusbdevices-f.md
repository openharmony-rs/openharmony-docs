# addDisallowedUsbDevices

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## addDisallowedUsbDevices

```TypeScript
function addDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void
```

Adds disallowed USB device types.

Use cases:

- Disable specific types of USB devices in enterprise security management scenarios.  
- Prevent data leaks by disabling USB storage device types.  
- Enable device administrators to prohibit the use of certain USB device types based on security policies.  
- Work with the [removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md) API to implement dynamic  
management of USB device types.

> **NOTE:** 
> 
> The [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md) API is recommended.
> A policy conflict is reported when this API is called in the following scenarios:

1. The USB capability of the device has been disabled via [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md).
2. The available USB devices have been added through [addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md).
3. The USB storage write capability has been disabled for specific users via [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md).
4. Disallowed USB device types have been added via [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md).

**Since:** 14

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| usbDevices | Array&lt;[UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md)&gt; | Yes | Array of the USB devices to be added, which can be obtained through [getDevices](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md). The maximum number of USB devices is 200. If there are already 100 USB device IDs, only 100 more can be added. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDevices: Array<usbManager.UsbDeviceType> = [{
    baseClass: 8,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.addDisallowedUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in adding disallowed USB devices.`);
} catch (err) {
  console.error(`Failed to add disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```
