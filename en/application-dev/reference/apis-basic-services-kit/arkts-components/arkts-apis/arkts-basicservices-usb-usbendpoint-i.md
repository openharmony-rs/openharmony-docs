# USBEndpoint

```TypeScript
interface USBEndpoint
```

Represents the USB endpoint from which data is sent or received. You can obtain the USB endpoint through [USBInterface](arkts-basicservices-usb-usbinterface-i.md).

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md)

<!--Device-usb-interface USBEndpoint--><!--Device-usb-interface USBEndpoint-End-->

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## address

```TypeScript
address: number
```

Endpoint address.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [address](arkts-basicservices-usbmanager-usbendpoint-i.md#address)

<!--Device-USBEndpoint-address: number--><!--Device-USBEndpoint-address: number-End-->

**System capability:** SystemCapability.USB.USBManager

## attributes

```TypeScript
attributes: number
```

Endpoint attributes.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [attributes](arkts-basicservices-usbmanager-usbendpoint-i.md#attributes)

<!--Device-USBEndpoint-attributes: number--><!--Device-USBEndpoint-attributes: number-End-->

**System capability:** SystemCapability.USB.USBManager

## direction

```TypeScript
direction: USBRequestDirection
```

Endpoint direction.

**Type:** [USBRequestDirection](arkts-basicservices-usb-usbrequestdirection-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [direction](arkts-basicservices-usbmanager-usbendpoint-i.md#direction)

<!--Device-USBEndpoint-direction: USBRequestDirection--><!--Device-USBEndpoint-direction: USBRequestDirection-End-->

**System capability:** SystemCapability.USB.USBManager

## interfaceId

```TypeScript
interfaceId: number
```

Unique ID of the interface to which the endpoint belongs.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [interfaceId](arkts-basicservices-usbmanager-usbendpoint-i.md#interfaceid)

<!--Device-USBEndpoint-interfaceId: number--><!--Device-USBEndpoint-interfaceId: number-End-->

**System capability:** SystemCapability.USB.USBManager

## interval

```TypeScript
interval: number
```

Endpoint interval.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [interval](arkts-basicservices-usbmanager-usbendpoint-i.md#interval)

<!--Device-USBEndpoint-interval: number--><!--Device-USBEndpoint-interval: number-End-->

**System capability:** SystemCapability.USB.USBManager

## maxPacketSize

```TypeScript
maxPacketSize: number
```

Maximum size of data packets on the endpoint.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [maxPacketSize](arkts-basicservices-usbmanager-usbendpoint-i.md#maxpacketsize)

<!--Device-USBEndpoint-maxPacketSize: number--><!--Device-USBEndpoint-maxPacketSize: number-End-->

**System capability:** SystemCapability.USB.USBManager

## number

```TypeScript
number: number
```

Endpoint number.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [number](arkts-basicservices-usbmanager-usbendpoint-i.md#number)

<!--Device-USBEndpoint-number: number--><!--Device-USBEndpoint-number: number-End-->

**System capability:** SystemCapability.USB.USBManager

## type

```TypeScript
type: number
```

Endpoint type.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [type](arkts-basicservices-usbmanager-usbendpoint-i.md#type)

<!--Device-USBEndpoint-type: number--><!--Device-USBEndpoint-type: number-End-->

**System capability:** SystemCapability.USB.USBManager
