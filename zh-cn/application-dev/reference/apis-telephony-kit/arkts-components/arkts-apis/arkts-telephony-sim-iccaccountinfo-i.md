# IccAccountInfo

```TypeScript
export interface IccAccountInfo
```

Icc账户信息。

**起始版本：** 10

<!--Device-sim-export interface IccAccountInfo--><!--Device-sim-export interface IccAccountInfo-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## iccId

```TypeScript
iccId: string
```

ICCID号码。

**类型：** string

**起始版本：** 10

<!--Device-IccAccountInfo-iccId: string--><!--Device-IccAccountInfo-iccId: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## isActive

```TypeScript
isActive: boolean
```

卡是否被激活。

- true:激活。  
- false：未激活。

**类型：** boolean

**起始版本：** 10

<!--Device-IccAccountInfo-isActive: boolean--><!--Device-IccAccountInfo-isActive: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## isEsim

```TypeScript
isEsim: boolean
```

标记卡是否是eSim。

- true:是eSim。  
- false：不是eSim。

**类型：** boolean

**起始版本：** 10

<!--Device-IccAccountInfo-isEsim: boolean--><!--Device-IccAccountInfo-isEsim: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## showName

```TypeScript
showName: string
```

SIM卡显示名称。

**类型：** string

**起始版本：** 10

<!--Device-IccAccountInfo-showName: string--><!--Device-IccAccountInfo-showName: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## showNumber

```TypeScript
showNumber: string
```

SIM卡显示号码。

**类型：** string

**起始版本：** 10

<!--Device-IccAccountInfo-showNumber: string--><!--Device-IccAccountInfo-showNumber: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## simId

```TypeScript
simId: number
```

SIM卡ID。

**类型：** number

**起始版本：** 10

<!--Device-IccAccountInfo-simId: int--><!--Device-IccAccountInfo-simId: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## slotIndex

```TypeScript
slotIndex: number
```

卡槽ID。

**类型：** number

**起始版本：** 10

<!--Device-IccAccountInfo-slotIndex: int--><!--Device-IccAccountInfo-slotIndex: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService
