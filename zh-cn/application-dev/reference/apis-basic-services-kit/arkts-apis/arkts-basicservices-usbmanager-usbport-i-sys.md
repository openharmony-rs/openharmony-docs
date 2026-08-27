# USBPort（系统接口）

USB设备端口。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## id

```TypeScript
id: number
```

USB端口唯一标识。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: USBPortStatus
```

USB端口角色信息。其currentMode应在supportedModes范围内。

**类型：** USBPortStatus

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## supportedModes

```TypeScript
supportedModes: PortModeType
```

USB端口所支持的模式的数字组合掩码。status.currentMode应在此范围内。

**类型：** PortModeType

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。
