# USBDevice

```TypeScript
interface USBDevice
```

Represents the USB device information.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## busNum

```TypeScript
busNum: number
```

Bus address.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

Device class code.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## configs

```TypeScript
configs: Array<USBConfiguration>
```

Device configuration descriptor information.

**Type:** Array&lt;[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)&gt;

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## devAddress

```TypeScript
devAddress: number
```

Device address.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## manufacturerName

```TypeScript
manufacturerName: string
```

Manufacturer name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

Device name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## productId

```TypeScript
productId: number
```

Product ID.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## productName

```TypeScript
productName: string
```

Product name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

Device protocol code.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## serial

```TypeScript
serial: string
```

Serial number. Third-party apps cannot obtain the device serial number from this field. This field is unavailable to third-party apps. To obtain the serial number, third-party apps need to request permissions to access the device and then initiate a control transfer.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

Device subclass code.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## vendorId

```TypeScript
vendorId: number
```

Vendor ID.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## version

```TypeScript
version: string
```

Version.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.USB.USBManager
