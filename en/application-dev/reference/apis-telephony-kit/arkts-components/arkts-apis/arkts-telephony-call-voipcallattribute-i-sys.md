# VoipCallAttribute (System API)

```TypeScript
export interface VoipCallAttribute
```

Defines the VoIP call information.

**Since:** 11

<!--Device-call-export interface VoipCallAttribute--><!--Device-call-export interface VoipCallAttribute-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name of the third-party application.

**Type:** string

**Since:** 11

<!--Device-VoipCallAttribute-abilityName: string--><!--Device-VoipCallAttribute-abilityName: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## extensionId

```TypeScript
extensionId: string
```

Process ID of the third-party application.

**Type:** string

**Since:** 11

<!--Device-VoipCallAttribute-extensionId: string--><!--Device-VoipCallAttribute-extensionId: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## isConferenceCall

```TypeScript
isConferenceCall?: boolean
```

Whether the call is a conference call.

**Type:** boolean

**Since:** 12

<!--Device-VoipCallAttribute-isConferenceCall?: boolean--><!--Device-VoipCallAttribute-isConferenceCall?: boolean-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## isVoiceAnswerSupported

```TypeScript
isVoiceAnswerSupported?: boolean
```

Whether call answering with voice commands is supported.

**Type:** boolean

**Since:** 12

<!--Device-VoipCallAttribute-isVoiceAnswerSupported?: boolean--><!--Device-VoipCallAttribute-isVoiceAnswerSupported?: boolean-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## showBannerForIncomingCall

```TypeScript
showBannerForIncomingCall?: boolean
```

Whether to display the incoming call banner.

**Type:** boolean

**Since:** 12

<!--Device-VoipCallAttribute-showBannerForIncomingCall?: boolean--><!--Device-VoipCallAttribute-showBannerForIncomingCall?: boolean-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## userName

```TypeScript
userName: string
```

User nickname.

**Type:** string

**Since:** 11

<!--Device-VoipCallAttribute-userName: string--><!--Device-VoipCallAttribute-userName: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## userProfile

```TypeScript
userProfile: image.PixelMap
```

User profile picture.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 11

<!--Device-VoipCallAttribute-userProfile: image.PixelMap--><!--Device-VoipCallAttribute-userProfile: image.PixelMap-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## voipBundleName

```TypeScript
voipBundleName: string
```

Bundle name of the third-party application.

**Type:** string

**Since:** 11

<!--Device-VoipCallAttribute-voipBundleName: string--><!--Device-VoipCallAttribute-voipBundleName: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## voipCallId

```TypeScript
voipCallId: string
```

Unique ID of a VoIP call.

**Type:** string

**Since:** 11

<!--Device-VoipCallAttribute-voipCallId: string--><!--Device-VoipCallAttribute-voipCallId: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
