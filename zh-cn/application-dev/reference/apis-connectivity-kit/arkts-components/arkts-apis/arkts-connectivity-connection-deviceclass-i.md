# DeviceClass

描述蓝牙设备的类型。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## classOfDevice

```TypeScript
classOfDevice: number
```

设备类型。是蓝牙标准协议中定义的类型字段，包含了[MajorClass](arkts-connectivity-constant-majorclass-e.md)、[MajorMinorClass](arkts-connectivity-constant-majorminorclass-e.md)和支持的主要服务这三种设备信息。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## majorClass

```TypeScript
majorClass: MajorClass
```

主要类型。是蓝牙标准协议中定义的类型字段。

**类型：** [MajorClass](arkts-connectivity-connection-majorclass-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## majorMinorClass

```TypeScript
majorMinorClass: MajorMinorClass
```

子类型，是在主要类型基础上进一步细分的类型。是蓝牙标准协议中定义的类型字段。

**类型：** [MajorMinorClass](arkts-connectivity-connection-majorminorclass-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
