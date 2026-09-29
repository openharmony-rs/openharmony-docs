# SignalInformation

```TypeScript
export interface SignalInformation
```

网络信号强度信息对象。

**起始版本：** 6

<!--Device-radio-export interface SignalInformation--><!--Device-radio-export interface SignalInformation-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## dBm

```TypeScript
dBm: number
```

网络信号强度，范围为[-140, 140]，超出范围返回错误。

**类型：** number

**起始版本：** 9

<!--Device-SignalInformation-dBm: int--><!--Device-SignalInformation-dBm: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## signalLevel

```TypeScript
signalLevel: number
```

网络信号强度等级，范围为[0, 5]，超出范围返回错误。

**类型：** number

**起始版本：** 6

<!--Device-SignalInformation-signalLevel: int--><!--Device-SignalInformation-signalLevel: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## signalType

```TypeScript
signalType: NetworkType
```

网络信号强度类型。

**类型：** [NetworkType](arkts-telephony-radio-networktype-e.md)

**起始版本：** 6

<!--Device-SignalInformation-signalType: NetworkType--><!--Device-SignalInformation-signalType: NetworkType-End-->

**系统能力：** SystemCapability.Telephony.CoreService
