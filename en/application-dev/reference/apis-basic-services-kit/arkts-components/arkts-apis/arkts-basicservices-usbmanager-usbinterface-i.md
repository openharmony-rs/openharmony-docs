# USBInterface

```TypeScript
interface USBInterface
```

Represents a USB interface. One [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) object can contain multiple **USBInterface** instances, each providing a specific function.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## alternateSetting

```TypeScript
alternateSetting: number
```

Alternative setting index of the interface, which is used to switch between multiple optional descriptors of the same interface. The value **0** indicates the default setting, and other values indicate specific alternative settings.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

Device type.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## endpoints

```TypeScript
endpoints: Array<USBEndpoint>
```

Endpoints that belong to the USB interface.

**Type:** Array&lt;[USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md)&gt;

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

Unique ID of the USB interface.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

Interface name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

Interface protocol.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

Device subclass.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager
