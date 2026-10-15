# VoIPCallStateInfo

```TypeScript
export interface VoIPCallStateInfo
```

VoIP呼叫状态信息。

**起始版本：** 26.0.1

<!--Device-observer-export interface VoIPCallStateInfo--><!--Device-observer-export interface VoIPCallStateInfo-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## 导入模块

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## appName

```TypeScript
appName: string
```

VoIP应用的名称。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-VoIPCallStateInfo-appName: string--><!--Device-VoIPCallStateInfo-appName: string-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## callState

```TypeScript
callState: VoIPCallState
```

表示VoIP呼叫的状态。

**类型：** [VoIPCallState](arkts-telephony-observer-voipcallstate-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-VoIPCallStateInfo-callState: VoIPCallState--><!--Device-VoIPCallStateInfo-callState: VoIPCallState-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## callType

```TypeScript
callType: VoIPCallType
```

VoIP呼叫类型。

**类型：** [VoIPCallType](arkts-telephony-observer-voipcalltype-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-VoIPCallStateInfo-callType: VoIPCallType--><!--Device-VoIPCallStateInfo-callType: VoIPCallType-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## contactName

```TypeScript
contactName: string
```

VoIP呼叫的联系人姓名。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-VoIPCallStateInfo-contactName: string--><!--Device-VoIPCallStateInfo-contactName: string-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## isVoiceAnswerSupported

```TypeScript
isVoiceAnswerSupported: boolean
```

指示VoIP应用程序是否支持将当前呼叫作为语音呼叫应答。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-VoIPCallStateInfo-isVoiceAnswerSupported: boolean--><!--Device-VoIPCallStateInfo-isVoiceAnswerSupported: boolean-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry
