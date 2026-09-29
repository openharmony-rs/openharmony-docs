# NetworkInformation（系统接口）

```TypeScript
export interface NetworkInformation
```

Obtains the network information.

**起始版本：** 6

<!--Device-radio-export interface NetworkInformation--><!--Device-radio-export interface NetworkInformation-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## operatorName

```TypeScript
operatorName: string
```

Indicates the name of the operator.

**类型：** string

**起始版本：** 6

<!--Device-NetworkInformation-operatorName: string--><!--Device-NetworkInformation-operatorName: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## operatorNumeric

```TypeScript
operatorNumeric: string
```

Indicates the number of the operator.

**类型：** string

**起始版本：** 6

<!--Device-NetworkInformation-operatorNumeric: string--><!--Device-NetworkInformation-operatorNumeric: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## radioTech

```TypeScript
radioTech: string
```

Indicates the radio Technology.

**类型：** string

**起始版本：** 6

<!--Device-NetworkInformation-radioTech: string--><!--Device-NetworkInformation-radioTech: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: NetworkInformationState
```

Indicates the status of network information.

**类型：** [NetworkInformationState](arkts-telephony-radio-networkinformationstate-e-sys.md)

**起始版本：** 6

<!--Device-NetworkInformation-state: NetworkInformationState--><!--Device-NetworkInformation-state: NetworkInformationState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
