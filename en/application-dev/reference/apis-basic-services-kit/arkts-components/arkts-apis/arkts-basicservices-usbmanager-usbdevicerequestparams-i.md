# USBDeviceRequestParams

Describes control transfer parameters.

**Since:** 12

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## bmRequestType

```TypeScript
bmRequestType: number
```

Request control type, which specifies the direction and type of the control transfer. The value must comply with the USB protocol specifications. Common values are as follows: **0x00**: standard request from the host to the device; **0x20**: class request from the host to the device; **0x40**: vendor request from the host to the device; 0x80: standard request from the device to the host.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.USB.USBManager

## bRequest

```TypeScript
bRequest: number
```

Request type, which indicates a specific USB control request command such as obtaining the descriptor or setting the address.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.USB.USBManager

## data

```TypeScript
data: Uint8Array
```

Buffer for writing or reading data. The array length must be equal to the number of data bytes specified by **wLength**. It is used to control data transmission or reception during data transfer.

**Type:** Uint8Array

**Since:** 12

**System capability:** SystemCapability.USB.USBManager

## wIndex

```TypeScript
wIndex: number
```

Index value corresponding to the request parameter **wValue**, which is used to specify the target interface or endpoint of the control request.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.USB.USBManager

## wLength

```TypeScript
wLength: number
```

Length of the request data, which is used to specify the number of data bytes expected to be received or sent during control transfer.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.USB.USBManager

## wValue

```TypeScript
wValue: number
```

Request parameter, which is used to transfer the parameters required by the control request to the USB device.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.USB.USBManager
