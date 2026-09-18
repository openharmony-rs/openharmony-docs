# CallAttributeOptions (System API)

Defines the call attribute options.

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## accountId

```TypeScript
accountId: number
```

Account ID.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## accountNumber

```TypeScript
accountNumber: string
```

Account number.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## callId

```TypeScript
callId: number
```

Call ID.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## callState

```TypeScript
callState: DetailedCallState
```

Detailed call state.

**Type:** [DetailedCallState](arkts-telephony-call-detailedcallstate-e-sys.md)

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## callType

```TypeScript
callType: CallType
```

Enumerates call types.

**Type:** [CallType](arkts-telephony-call-calltype-e-sys.md)

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## conferenceState

```TypeScript
conferenceState: ConferenceState
```

Enumerates conference states.

**Type:** [ConferenceState](arkts-telephony-call-conferencestate-e-sys.md)

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## crsType

```TypeScript
crsType: number
```

Video RBT type.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## extraParams

```TypeScript
extraParams?: Record<string, Object>
```

Indicates the extra call parameters.

**Type:** Record&lt;string, Object&gt;

**Since:** 14

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## isCustomAccessibility

```TypeScript
isCustomAccessibility?: boolean
```

Indicates is custom accessibility enabled.

**Type:** boolean

**Since:** 26.0.0

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## isEcc

```TypeScript
isEcc: boolean
```

Whether the call is an ECC. The default value is **false**.

- **true**: yes  
- **false**: no

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## numberLocation

```TypeScript
numberLocation?: string
```

Home location area of the number.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## numberMarkInfo

```TypeScript
numberMarkInfo?: NumberMarkInfo
```

Number mark.

**Type:** [NumberMarkInfo](arkts-telephony-call-numbermarkinfo-i-sys.md)

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## originalCallType

```TypeScript
originalCallType: number
```

Original call type of the Video RBT service.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## rttState

```TypeScript
rttState?: RttState
```

Indicates the rtt state.

**Type:** [RttState](arkts-telephony-call-rttstate-e-sys.md)

**Since:** 22

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## speakerphoneOn

```TypeScript
speakerphoneOn: boolean
```

Whether the speakerphone is used to answer a call. The default value is **false**.

- **true**: yes  
- **false**: no

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## startTime

```TypeScript
startTime: number
```

Start time.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## videoState

```TypeScript
videoState: VideoStateType
```

Video state type.

**Type:** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## voipCallAttribute

```TypeScript
voipCallAttribute?: VoipCallAttribute
```

Defines the VoIP call information.

**Type:** [VoipCallAttribute](arkts-telephony-call-voipcallattribute-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## xCallType

```TypeScript
xCallType?: XCallType
```

X-Call type.

**Type:** [XCallType](arkts-telephony-call-xcalltype-e-sys.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
