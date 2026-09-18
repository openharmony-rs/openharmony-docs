# USBPortStatus（系统接口）

USB设备端口角色信息。currentMode表示端口的当前USB模式，其值应在USBPort的supportedModes范围内。currentPowerRole表示当前电源角色，currentDataRole表示当前数据传输角色。这些字段之间存在对应关系：在DFP模式下，dataRole通常为HOST、powerRole通常为SOURCE；在UFP模式下，dataRole通常为DEVICE、powerRole通常为SINK。端口状态变更受硬件和系统约束，某些模式或角色组合可能不被支持。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## currentDataRole

```TypeScript
currentDataRole: number
```

当前设备数据传输角色，取值参见[DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md)。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## currentMode

```TypeScript
currentMode: number
```

当前的USB模式，取值参见[PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md)。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## currentPowerRole

```TypeScript
currentPowerRole: number
```

当前设备电源角色，取值参见[PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md)。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。
