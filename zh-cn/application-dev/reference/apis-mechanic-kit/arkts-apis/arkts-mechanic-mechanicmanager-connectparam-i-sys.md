# ConnectParam（系统接口）

连接参数定义

**起始版本：** 26.0.0

<!--Device-mechanicManager-export interface ConnectParam--><!--Device-mechanicManager-export interface ConnectParam-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## custdata

```TypeScript
custdata: string
```

发现设备时携带的数据数据必须符合以下格式：|类型|值|类型|值|。每个特定类型的value'len是预定义的长度支持的类型和版本如下表所示。  
-----------------------------------------------------------------类型|值|值len |api级别  
-----------------------------------------------------------------0x01 |三轴重力传感器值| 3Byte |26.0.0  
-----------------------------------------------------------------0x02|MAC地址第1字节偏移|1字节|26.0.0  
-----------------------------------------------------------------0x03 |配对广播|1字节|26.0.0  
-----------------------------------------------------------------0x04 |目标设备标识|4字节|26.0.0  
-----------------------------------------------------------------。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectParam-custdata: string--><!--Device-ConnectParam-custdata: string-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName?: string
```

具身设备名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectParam-deviceName?: string--><!--Device-ConnectParam-deviceName?: string-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

## identifier

```TypeScript
identifier?: number
```

当前设备标识。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectParam-identifier?: int--><!--Device-ConnectParam-identifier?: int-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

