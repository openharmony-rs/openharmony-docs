# UsbTransferStatus

```TypeScript
export enum UsbTransferStatus
```

Enumerates the status code returned after data processing is complete.

**Since:** 18

<!--Device-usbManager-export enum UsbTransferStatus--><!--Device-usbManager-export enum UsbTransferStatus-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_COMPLETED

```TypeScript
TRANSFER_COMPLETED = 0
```

Transfer completed.

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_COMPLETED = 0--><!--Device-UsbTransferStatus-TRANSFER_COMPLETED = 0-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_ERROR

```TypeScript
TRANSFER_ERROR = 1
```

Transfer failed.

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_ERROR = 1--><!--Device-UsbTransferStatus-TRANSFER_ERROR = 1-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_TIMED_OUT

```TypeScript
TRANSFER_TIMED_OUT = 2
```

Transfer timed out.

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_TIMED_OUT = 2--><!--Device-UsbTransferStatus-TRANSFER_TIMED_OUT = 2-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_CANCELED

```TypeScript
TRANSFER_CANCELED = 3
```

Transfer canceled.

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_CANCELED = 3--><!--Device-UsbTransferStatus-TRANSFER_CANCELED = 3-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_STALL

```TypeScript
TRANSFER_STALL = 4
```

Stall detected (bulk/interrupt endpoint).

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_STALL = 4--><!--Device-UsbTransferStatus-TRANSFER_STALL = 4-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_NO_DEVICE

```TypeScript
TRANSFER_NO_DEVICE = 5
```

Device disconnected.

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_NO_DEVICE = 5--><!--Device-UsbTransferStatus-TRANSFER_NO_DEVICE = 5-End-->

**System capability:** SystemCapability.USB.USBManager

## TRANSFER_OVERFLOW

```TypeScript
TRANSFER_OVERFLOW = 6
```

Device sent more data than requested.

**Since:** 18

<!--Device-UsbTransferStatus-TRANSFER_OVERFLOW = 6--><!--Device-UsbTransferStatus-TRANSFER_OVERFLOW = 6-End-->

**System capability:** SystemCapability.USB.USBManager
