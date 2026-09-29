# NetworkState

```TypeScript
export interface NetworkState
```

网络注册状态。

**起始版本：** 6

<!--Device-radio-export interface NetworkState--><!--Device-radio-export interface NetworkState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## cfgTech

```TypeScript
cfgTech: RadioTechnology
```

设备的无线接入技术。

**类型：** [RadioTechnology](arkts-telephony-radio-radiotechnology-e.md)

**起始版本：** 8

<!--Device-NetworkState-cfgTech: RadioTechnology--><!--Device-NetworkState-cfgTech: RadioTechnology-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## isCaActive

```TypeScript
isCaActive: boolean
```

CA的状态。

**类型：** boolean

**起始版本：** 6

<!--Device-NetworkState-isCaActive: boolean--><!--Device-NetworkState-isCaActive: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## isEmergency

```TypeScript
isEmergency: boolean
```

此设备是否只允许拨打紧急呼叫。

**类型：** boolean

**起始版本：** 6

<!--Device-NetworkState-isEmergency: boolean--><!--Device-NetworkState-isEmergency: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## isRoaming

```TypeScript
isRoaming: boolean
```

是否处于漫游状态。

**类型：** boolean

**起始版本：** 6

<!--Device-NetworkState-isRoaming: boolean--><!--Device-NetworkState-isRoaming: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## longOperatorName

```TypeScript
longOperatorName: string
```

注册网络的长运营商名称。

**类型：** string

**起始版本：** 6

<!--Device-NetworkState-longOperatorName: string--><!--Device-NetworkState-longOperatorName: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## nsaState

```TypeScript
nsaState: NsaState
```

设备的NSA网络注册状态。

**类型：** [NsaState](arkts-telephony-radio-nsastate-e.md)

**起始版本：** 6

<!--Device-NetworkState-nsaState: NsaState--><!--Device-NetworkState-nsaState: NsaState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## plmnNumeric

```TypeScript
plmnNumeric: string
```

注册网络的PLMN码。

**类型：** string

**起始版本：** 6

<!--Device-NetworkState-plmnNumeric: string--><!--Device-NetworkState-plmnNumeric: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## regState

```TypeScript
regState: RegState
```

设备的网络注册状态。

**类型：** [RegState](arkts-telephony-radio-regstate-e.md)

**起始版本：** 6

<!--Device-NetworkState-regState: RegState--><!--Device-NetworkState-regState: RegState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## shortOperatorName

```TypeScript
shortOperatorName: string
```

注册网络的短运营商名称。

**类型：** string

**起始版本：** 6

<!--Device-NetworkState-shortOperatorName: string--><!--Device-NetworkState-shortOperatorName: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService
