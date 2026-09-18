# USBAccessoryHandle

USB配件句柄，包含配件文件描述符，用于通过CoreFileKit提供的read/write接口和配件进行通信。

**起始版本：** 14

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## accessoryFd

```TypeScript
accessoryFd: number
```

配件文件描述符。合法的accessoryFd是正整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.USB.USBManager
