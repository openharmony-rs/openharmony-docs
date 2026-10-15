# VoIPCallStateInfo

```TypeScript
export interface VoIPCallStateInfo
```

Indicates VoIP call state information.

**Since:** 26.0.1

<!--Device-observer-export interface VoIPCallStateInfo--><!--Device-observer-export interface VoIPCallStateInfo-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## appName

```TypeScript
appName: string
```

Indicates the name of the VoIP application.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-VoIPCallStateInfo-appName: string--><!--Device-VoIPCallStateInfo-appName: string-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## callState

```TypeScript
callState: VoIPCallState
```

Indicates the state of the VoIP call.

**Type:** [VoIPCallState](arkts-telephony-observer-voipcallstate-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-VoIPCallStateInfo-callState: VoIPCallState--><!--Device-VoIPCallStateInfo-callState: VoIPCallState-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## callType

```TypeScript
callType: VoIPCallType
```

Indicates the type of the VoIP call.

**Type:** [VoIPCallType](arkts-telephony-observer-voipcalltype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-VoIPCallStateInfo-callType: VoIPCallType--><!--Device-VoIPCallStateInfo-callType: VoIPCallType-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## contactName

```TypeScript
contactName: string
```

Indicates the contact name of the VoIP call.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-VoIPCallStateInfo-contactName: string--><!--Device-VoIPCallStateInfo-contactName: string-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

## isVoiceAnswerSupported

```TypeScript
isVoiceAnswerSupported: boolean
```

Indicates whether the VoIP application supports answering the current call as a voice call.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-VoIPCallStateInfo-isVoiceAnswerSupported: boolean--><!--Device-VoIPCallStateInfo-isVoiceAnswerSupported: boolean-End-->

**System capability:** SystemCapability.Telephony.StateRegistry
