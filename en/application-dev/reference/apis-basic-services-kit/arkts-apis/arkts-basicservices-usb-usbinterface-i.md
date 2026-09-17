# USBInterface

Represents a USB interface. One [USBConfig](arkts-basicservices-usb-usbconfig-i.md) can contain multiple **USBInterface** instances, each providing a specific function.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md)

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## alternateSetting

```TypeScript
alternateSetting: number
```

Settings for alternating between descriptors of the same USB interface.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [alternateSetting](arkts-basicservices-usbmanager-usbinterface-i.md#alternatesetting)

**System capability:** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: number
```

Device type.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clazz](arkts-basicservices-usbmanager-usbinterface-i.md#clazz)

**System capability:** SystemCapability.USB.USBManager

## endpoints

```TypeScript
endpoints: Array<USBEndpoint>
```

Endpoints that belong to the USB interface.

**Type:** Array&lt;[USBEndpoint](arkts-basicservices-usb-usbendpoint-i.md)&gt;

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [endpoints](arkts-basicservices-usbmanager-usbinterface-i.md#endpoints)

**System capability:** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

Unique ID of the USB interface.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [id](arkts-basicservices-usbmanager-usbinterface-i.md#id)

**System capability:** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

Interface name.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [name](arkts-basicservices-usbmanager-usbinterface-i.md#name)

**System capability:** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: number
```

Interface protocol.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [protocol](arkts-basicservices-usbmanager-usbinterface-i.md#protocol)

**System capability:** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: number
```

Device subclass.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [subClass](arkts-basicservices-usbmanager-usbinterface-i.md#subclass)

**System capability:** SystemCapability.USB.USBManager
