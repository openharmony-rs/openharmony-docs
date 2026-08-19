# USBAccessoryHandle

USB配件句柄，包含配件文件描述符，用于通过CoreFileKit提供的read/write接口和配件进行通信。

**起始版本：** 23

<!--Device-usbManager-interface USBAccessoryHandle--><!--Device-usbManager-interface USBAccessoryHandle-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## accessoryFd

```TypeScript
accessoryFd: int
```

配件文件描述符。合法的accessoryFd是正整数。

**类型：** int

**起始版本：** 23

<!--Device-USBAccessoryHandle-accessoryFd: int--><!--Device-USBAccessoryHandle-accessoryFd: int-End-->

**系统能力：** SystemCapability.USB.USBManager

