# USBDeviceInfo (System API)

Defines detailed information about the USB device. It is inherited from [DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md).

**Inheritance/Implementation:** USBDeviceInfo extends [DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md)

**Since:** 12

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## interfaceDescList

```TypeScript
interfaceDescList: Array<Readonly<USBInterfaceDesc>>
```

List of interface descriptors of the USB device.

**Type:** Array&lt;Readonly&lt;[USBInterfaceDesc](arkts-driverdevelopment-devicemanager-usbinterfacedesc-i-sys.md)&gt;&gt;

**Since:** 12

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## productId

```TypeScript
productId: number
```

Product ID of the USB device.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.

## vendorId

```TypeScript
vendorId: number
```

Vendor ID of the USB device.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Driver.ExternalDevice

**System API:** This is a system API.
