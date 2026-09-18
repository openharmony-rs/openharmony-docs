# @ohos.usb(USB Manager)

The **usb** module provides USB device management functions, including USB device list query, bulk data transfer, control transfer, and permission control.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with
> a superscript to indicate their earliest API version.
> The APIs provided by this module are no longer maintained since API version 9. You are advised to use
> [@ohos.usbManager](arkts-basicservices-usbmanager.md).

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [usbManager](arkts-basicservices-usbmanager.md)

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [bulkTransfer](arkts-basicservices-usb-bulktransfer-f.md) | Performs bulk transfer. |
| [claimInterface](arkts-basicservices-usb-claiminterface-f.md) | Claims a USB interface. |
| [closePipe](arkts-basicservices-usb-closepipe-f.md) | Closes a USB device pipe. |
| [connectDevice](arkts-basicservices-usb-connectdevice-f.md) | Connects to a USB device. |
| [controlTransfer](arkts-basicservices-usb-controltransfer-f.md) | Performs control transfer. |
| [getDevices](arkts-basicservices-usb-getdevices-f.md) | Obtains the USB device list. |
| [getFileDescriptor](arkts-basicservices-usb-getfiledescriptor-f.md) | Obtains the file descriptor. |
| [getRawDescriptor](arkts-basicservices-usb-getrawdescriptor-f.md) | Obtains the raw USB descriptor. |
| [hasRight](arkts-basicservices-usb-hasright-f.md) | Checks whether the application has the permission to access the device. |
| [releaseInterface](arkts-basicservices-usb-releaseinterface-f.md) | Releases a USB interface. |
| [requestRight](arkts-basicservices-usb-requestright-f.md) | Requests the temporary permission for the application to access a USB device. This API uses a promise to return the result. System applications are granted the device access permission by default, and you do not need to apply for the permission separately. |
| [setConfiguration](arkts-basicservices-usb-setconfiguration-f.md) | Sets the device configuration. |
| [setInterface](arkts-basicservices-usb-setinterface-f.md) | Sets a USB interface. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getCurrentFunctions](arkts-basicservices-usb-getcurrentfunctions-f-sys.md) | Obtains the numeric mask combination for the USB function list in Device mode. |
| [getPorts](arkts-basicservices-usb-getports-f-sys.md) | Obtains the list of all physical USB ports. |
| [getSupportedModes](arkts-basicservices-usb-getsupportedmodes-f-sys.md) | Obtains the mask combination for the supported mode list of a given USB port. |
| [setCurrentFunctions](arkts-basicservices-usb-setcurrentfunctions-f-sys.md) | Sets the current USB function list in Device mode. |
| [setPortRoles](arkts-basicservices-usb-setportroles-f-sys.md) | Sets the role types supported by a specified port, which can be **powerRole** (for charging) and **dataRole** (for data transfer). |
| [usbFunctionsFromString](arkts-basicservices-usb-usbfunctionsfromstring-f-sys.md) | Converts the USB function list in the string format to a numeric mask in Device mode. |
| [usbFunctionsToString](arkts-basicservices-usb-usbfunctionstostring-f-sys.md) | Converts the USB function list in the numeric mask format to a string in Device mode. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [USBConfig](arkts-basicservices-usb-usbconfig-i.md) | Represents the USB configuration. One [USBDevice](arkts-basicservices-usb-usbdevice-i.md) can contain multiple **USBConfig** instances. |
| [USBControlParams](arkts-basicservices-usb-usbcontrolparams-i.md) | Represents control transfer parameters. |
| [USBDevice](arkts-basicservices-usb-usbdevice-i.md) | Represents the USB device information. |
| [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | Represents a USB device pipe, which is used to determine a USB device. |
| [USBEndpoint](arkts-basicservices-usb-usbendpoint-i.md) | Represents the USB endpoint from which data is sent or received. You can obtain the USB endpoint through [USBInterface](arkts-basicservices-usb-usbinterface-i.md). |
| [USBInterface](arkts-basicservices-usb-usbinterface-i.md) | Represents a USB interface. One [USBConfig](arkts-basicservices-usb-usbconfig-i.md) can contain multiple **USBInterface** instances, each providing a specific function. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [USBPort](arkts-basicservices-usb-usbport-i-sys.md) | Represents a USB port. |
| [USBPortStatus](arkts-basicservices-usb-usbportstatus-i-sys.md) | Enumerates USB port roles. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [USBControlRequestType](arkts-basicservices-usb-usbcontrolrequesttype-e.md) | Enumerates control request types. |
| [USBRequestDirection](arkts-basicservices-usb-usbrequestdirection-e.md) | Enumerates request directions. |
| [USBRequestTargetType](arkts-basicservices-usb-usbrequesttargettype-e.md) | Enumerates request target types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DataRoleType](arkts-basicservices-usb-dataroletype-e-sys.md) | Enumerates data role types. |
| [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | Enumerates USB device function types. |
| [PortModeType](arkts-basicservices-usb-portmodetype-e-sys.md) | Enumerates USB port mode types. |
| [PowerRoleType](arkts-basicservices-usb-powerroletype-e-sys.md) | Enumerates power role types. |
<!--DelEnd-->
