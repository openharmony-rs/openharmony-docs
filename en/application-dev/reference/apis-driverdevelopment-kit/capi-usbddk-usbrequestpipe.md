# UsbRequestPipe
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-04T04:07:16.105Z pushedAt=2026-11-04T10:12:50.052Z nl=1 -->

```c
typedef struct UsbRequestPipe {...} __attribute__((aligned(8))) UsbRequestPipe
```

## Overview

Defines a request pipe, which is actually a USB data transfer request. It describes the basic configuration parameters for USB data transfer, including the interface handle, endpoint address, and timeout interval. This API applies to scenarios where USB data transfer is required.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t interfaceHandle | Interface handle, which identifies an interface on the USB device. The handle is obtained by calling [OH_Usb_ClaimInterface](capi-usb-ddk-api-h.md#oh_usb_claiminterface). |
| uint32_t timeout | Timeout interval, in milliseconds. The value **0** indicates that the operation is performed until it is complete. A non-zero value indicates that the operation times out if it is not complete within the specified milliseconds. |
| uint8_t endpoint | Endpoint address.|


