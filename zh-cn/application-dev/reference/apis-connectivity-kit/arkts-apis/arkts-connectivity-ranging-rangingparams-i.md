# RangingParams

测距参数，用于指定主动测距的目标设备和测距类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## capabilityType

```TypeScript
capabilityType: RangingTypes
```

测距能力类型，用于指定使用的测距技术。该参数必须要填入定义的有效值，否则引用该参数的接口会抛出34900052错误。

**类型：** [RangingTypes](arkts-connectivity-ranging-rangingtypes-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## deviceId

```TypeScript
deviceId: string
```

目标测距设备的地址，格式为xx:xx:xx:xx:xx:xx，其中x为十六进制数字，范围为0~9和A~F，分隔符为冒号，示例："11:22:33:44:55:66"。该参数需要按照指定格式填写，如果填入的参数不合法，会抛出34900054的错误码。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
