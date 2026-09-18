# USBConfig

Represents the USB configuration. One [USBDevice](arkts-basicservices-usb-usbdevice-i.md) can contain multiple **USBConfig** instances.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md)

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## attributes

```TypeScript
attributes: number
```

Configuration attributes.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [attributes](arkts-basicservices-usbmanager-usbconfiguration-i.md#attributes)

**System capability:** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

Unique ID of the USB configuration.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [id](arkts-basicservices-usbmanager-usbconfiguration-i.md#id)

**System capability:** SystemCapability.USB.USBManager

## interfaces

```TypeScript
interfaces: Array<USBInterface>
```

Supported interface attributes.

**Type:** Array&lt;[USBInterface](arkts-basicservices-usb-usbinterface-i.md)&gt;

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [interfaces](arkts-basicservices-usbmanager-usbconfiguration-i.md#interfaces)

**System capability:** SystemCapability.USB.USBManager

## isRemoteWakeup

```TypeScript
isRemoteWakeup: boolean
```

Support for remote wakeup.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isRemoteWakeup](arkts-basicservices-usbmanager-usbconfiguration-i.md#isremotewakeup)

**System capability:** SystemCapability.USB.USBManager

## isSelfPowered

```TypeScript
isSelfPowered: boolean
```

Support for independent power supplies.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSelfPowered](arkts-basicservices-usbmanager-usbconfiguration-i.md#isselfpowered)

**System capability:** SystemCapability.USB.USBManager

## maxPower

```TypeScript
maxPower: number
```

Maximum power consumption, in mA.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [maxPower](arkts-basicservices-usbmanager-usbconfiguration-i.md#maxpower)

**System capability:** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

Configuration name, which can be left empty.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [name](arkts-basicservices-usbmanager-usbconfiguration-i.md#name)

**System capability:** SystemCapability.USB.USBManager
