# USBAccessoryHandle

```TypeScript
interface USBAccessoryHandle
```

Defines a USB accessory handle, including the accessory file descriptor. This API is used to communicate with the accessory through the **read** or **write** API provided by Core File Kit.

**Since:** 14

<!--Device-usbManager-interface USBAccessoryHandle--><!--Device-usbManager-interface USBAccessoryHandle-End-->

**System capability:** SystemCapability.USB.USBManager

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## accessoryFd

```TypeScript
accessoryFd: number
```

Accessory file descriptor. A valid **accessoryFd** is a positive integer.

**Type:** number

**Since:** 14

<!--Device-USBAccessoryHandle-accessoryFd: int--><!--Device-USBAccessoryHandle-accessoryFd: int-End-->

**System capability:** SystemCapability.USB.USBManager
