# SerialPort

串口参数。

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## deviceName

```TypeScript
deviceName: string
```

串口设备的名称，用于显示和识别具体的串口设备。可用于在用户界面中展示设备信息，帮助用户区分不同的串口设备。

**类型：** string

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## portId

```TypeScript
portId: number
```

串口端口号，用于唯一标识串口设备。该值来自getPortList返回的SerialPort对象，用于指定要操作的串口设备。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial
