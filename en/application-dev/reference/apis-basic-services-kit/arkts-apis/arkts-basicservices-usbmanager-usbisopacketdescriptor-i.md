# UsbIsoPacketDescriptor

Describes packet information returned in real time by the transfer callback.

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## actualLength

```TypeScript
actualLength: number
```

Actual length of the read/write operation, in bytes.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## length

```TypeScript
length: number
```

Expected length of the read/write operation, in bytes.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## status

```TypeScript
status: UsbTransferStatus
```

Status code of the isochronous transfer subpacket.

**Type:** [UsbTransferStatus](arkts-basicservices-usbmanager-usbtransferstatus-e.md)

**Since:** 18

**System capability:** SystemCapability.USB.USBManager
