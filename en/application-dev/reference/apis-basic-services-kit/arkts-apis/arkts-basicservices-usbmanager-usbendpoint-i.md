# USBEndpoint

```TypeScript
interface USBEndpoint
```

Defines a USB endpoint, which is used for data transfer between the host and the USB device. You can obtain the USB endpoint through [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md).

> **Note:** 
> 
> The host controller schedules endpoints based on their types. Different scheduling policies are
> used for different types of endpoints. Bandwidth sharing scheduling is used for bulk endpoints,
> which is suitable for non-real-time transmission of a large amount of data. Fixed polling
> scheduling is used for interrupt endpoints, which is suitable for real-time transmission of a
> small amount of data. Bandwidth reservation scheduling is used for isochronous endpoints, which
> is suitable for real-time data streams such as audio and video.
> 
> The transmission characteristics, including the data packet format, error processing mechanism,
> and timeout policy, are determined based on the endpoint type during protocol layer packaging.
> ![USBEndpoint](../../../reference/figures/USBEndpoint.png)

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## address

```TypeScript
address: number
```

Endpoint address.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## attributes

```TypeScript
attributes: number
```

Endpoint attributes, indicating the transfer characteristics of the endpoint, including the transfer type (bulk, interrupt, or isochronous) and synchronization type. The value must comply with the USB endpoint descriptor specifications.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## direction

```TypeScript
direction: USBRequestDirection
```

Endpoint direction.

**Type:** [USBRequestDirection](arkts-basicservices-usbmanager-usbrequestdirection-e.md)

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## interfaceId

```TypeScript
interfaceId: number
```

Unique ID of the interface to which the endpoint belongs.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## interval

```TypeScript
interval: number
```

Endpoint interval, in milliseconds. This parameter indicates the interval for interrupt and isochronous endpoints. This field is not used for bulk endpoints.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## maxPacketSize

```TypeScript
maxPacketSize: number
```

Maximum size of data packets on the endpoint, in bytes.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## number

```TypeScript
number: number
```

Endpoint number.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

## type

```TypeScript
type: number
```

Endpoint type. For details, see [UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.USB.USBManager
