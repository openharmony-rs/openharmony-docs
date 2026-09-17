# claimInterfaceExclusive

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## claimInterfaceExclusive

```TypeScript
function claimInterfaceExclusive(pipe: USBDevicePipe, iface: USBInterface, force?: boolean,
    onConflict?: Callback<InterfaceConflictInfo>): void
```

Claims a USB device interface exclusively. When this API is called, the system checks whether the specified USB interface has been claimed by another process to avoid conflicts during declaration. If **force** is set to **true**, the operating system first releases the interface from the kernel driver and then grants control to the calling app. After the interface is claimed exclusively, other processes can still claim the same interface by calling [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md). You can use the **onConflict** callback to receive such conflict notifications.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the bus address and device address. You need to call [usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md) to obtain its value. |
| iface | [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md) | Yes | Index of the target USB interface. You can call [usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md) to obtain the device information and identify the USB interface based on the ID. |
| force | boolean | No | Whether to forcibly claim the USB interface. The default value is **false**, indicating that the USB interface is not forcibly claimed. You can set this parameter as required.<br>The default value is **false**. |
| onConflict | [Callback](arkts-basicservices-base-callback-i.md)&lt;[InterfaceConflictInfo](arkts-basicservices-usbmanager-interfaceconflictinfo-i.md)&gt; | No | Callback used to return the conflict information when other processes claim the same USB interface by calling [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) non-exclusively after the interface is claimed exclusively. If this parameter is not specified, no notification is sent when such a conflict occurs. <br>Default value: no callback is triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14400001](../errorcode-usb.md#14400001-usb-device-connection-denied) | Permission denied. |
| [14400004](../errorcode-usb.md#14400004-service-exception) | Service exception. |
| [14400007](../errorcode-usb.md#14400007-resource-busy) | Resource busy. Possible cause: The interface is claimed by another program or driver. |
| [14400010](../errorcode-usb.md#14400010-unrecognized-error) | USB driver error. Possible causes: <br>1. The device is not connected using [usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md). <br>2. The USB device state is abnormal. |
