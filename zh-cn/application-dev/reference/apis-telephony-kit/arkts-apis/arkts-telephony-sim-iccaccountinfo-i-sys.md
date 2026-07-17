# IccAccountInfo

Defines the ICC account information.

**起始版本：** 10

<!--Device-sim-export interface IccAccountInfo--><!--Device-sim-export interface IccAccountInfo-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## operatorName

```TypeScript
operatorName?: string
```

表示卡的操作员名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IccAccountInfo-operatorName?: string--><!--Device-IccAccountInfo-operatorName?: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## simLabelIndex

```TypeScript
simLabelIndex?: number
```

卡的simLabelIndex。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IccAccountInfo-simLabelIndex?: int--><!--Device-IccAccountInfo-simLabelIndex?: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

