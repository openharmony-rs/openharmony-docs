# @ohos.enterprise.usbManager(USB Management)

The **usbManager** module provides APIs for USB management.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).
> 
> The global restriction policy is provided by **restrictions**. To disable USB globally, see
> [@ohos.enterprise.restrictions (restriction policy)](arkts-mdm-enterprise-restrictions.md).

**Since:** 12

<!--Device-unnamed-declare namespace usbManager--><!--Device-unnamed-declare namespace usbManager-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addAllowedOpticalDiscDriveBurnUsbDevices](arkts-mdm-usbmanager-addallowedopticaldiscdriveburnusbdevices-f.md#addallowedopticaldiscdriveburnusbdevices) | Add the list of USB devices that support CD/DVD burning. |
| [addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addallowedusbdevices) | Adds allowed USB devices. |
| [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md#adddisallowedpermissiveusbdevices) | Adds disallowed USB device types. Unlike the [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md) API, this API does not require matching based on the [defined-class-codes](https://www.usb.org/defined-class-codes) standard. This API takes effect immediately on connected USB devices without requiring re-plugging. For example, if a USB wired headset is in normal use and this API is called to disable it, the headset will become unavailable immediately. |
| [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices) | Adds disallowed USB device types. |
| [getAllowedOpticalDiscDriveBurnUsbDevices](arkts-mdm-usbmanager-getallowedopticaldiscdriveburnusbdevices-f.md#getallowedopticaldiscdriveburnusbdevices) | Obtain the list of USB devices that support CD/DVD burning. |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices1) | Obtains allowed USB devices. |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices2) | Obtains allowed USB devices. |
| [getDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-getdisallowedpermissiveusbdevices-f.md#getdisallowedpermissiveusbdevices) | Obtains the USB device types that have been disallowed via [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md). |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices1) | Obtains the disallowed USB device types. |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices2) | Obtains the disallowed USB device types. |
| [getExternalStorageDeviceInfos](arkts-mdm-usbmanager-getexternalstoragedeviceinfos-f.md#getexternalstoragedeviceinfos) | Obtain the volume information of the current device. |
| [getUsbSerialNumber](arkts-mdm-usbmanager-getusbserialnumber-f.md#getusbserialnumber) | Queries the serial number of the usb device. |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy1) | Obtains the access policy of the USB storage device. |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy2) | Obtains the USB storage device (baseClass = 0x08) access policy. |
| [isExternalStorageInterceptEnable](arkts-mdm-usbmanager-isexternalstorageinterceptenable-f.md#isexternalstorageinterceptenable) | Query the enabling status of external storage device mounting. |
| [removeAllowedOpticalDiscDriveBurnUsbDevices](arkts-mdm-usbmanager-removeallowedopticaldiscdriveburnusbdevices-f.md#removeallowedopticaldiscdriveburnusbdevices) | Remove the list of USB devices that support CD/DVD burning. |
| [removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md#removeallowedusbdevices) | Removes allowed USB devices. |
| [removeDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-removedisallowedpermissiveusbdevices-f.md#removedisallowedpermissiveusbdevices) | Removes the USB device types that have been disallowed via [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md). The removed USB device types can be used normally. |
| [removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices) | Removes the disallowed USB device types. |
| [setExternalStorageDeviceMountPolicy](arkts-mdm-usbmanager-setexternalstoragedevicemountpolicy-f.md#setexternalstoragedevicemountpolicy) | Set the mounting policy for external storage devices. |
| [setExternalStorageInterceptEnable](arkts-mdm-usbmanager-setexternalstorageinterceptenable-f.md#setexternalstorageinterceptenable) | Set the enabling status of external storage device mounting. |
| [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy) | Sets the USB storage device (baseClass = 0x08) access policy. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [disableUsb](arkts-mdm-usbmanager-disableusb-f-sys.md#disableusb) | Enables or disables USB. |
| [isUsbDisabled](arkts-mdm-usbmanager-isusbdisabled-f-sys.md#isusbdisabled) | Queries whether the USB is disabled. |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy1) | Sets the USB read/write policy. This API uses an asynchronous callback to return the result. |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy2) | Sets the USB read/write policy. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PermissiveUsbDeviceType](arkts-mdm-usbmanager-permissiveusbdevicetype-i.md) | USB device type information. Partial field matching is supported. |
| [UsbDevice](arkts-mdm-usbmanager-usbdevice-i.md) | Represents the USB device identity information. |
| [UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md) | Represents the USB device identity information. |
| [UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md) | Represents the USB device type information. |

### Enums

| Name | Description |
| --- | --- |
| [Descriptor](arkts-mdm-usbmanager-descriptor-e.md) | Enumerates USB descriptors. |
| [MountPolicy](arkts-mdm-usbmanager-mountpolicy-e.md) | Mounting strategy. |
| [UsbPolicy](arkts-mdm-usbmanager-usbpolicy-e.md) | Enumerates the USB storage device access policies. |
