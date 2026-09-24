# SubmitTransferCallback

```TypeScript
interface SubmitTransferCallback
```

Transfers USB data packets in an asynchronous manner.

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

## isoPacketDescs

```TypeScript
isoPacketDescs: Array<Readonly<UsbIsoPacketDescriptor>>
```

Packet information of the isochronous transfer.

**Type:** Array&lt;Readonly&lt;[UsbIsoPacketDescriptor](arkts-basicservices-usbmanager-usbisopacketdescriptor-i.md)&gt;&gt;

**Since:** 18

**System capability:** SystemCapability.USB.USBManager

## status

```TypeScript
status: UsbTransferStatus
```

Status of the read/write operation.

**Type:** [UsbTransferStatus](arkts-basicservices-usbmanager-usbtransferstatus-e.md)

**Since:** 18

**System capability:** SystemCapability.USB.USBManager
