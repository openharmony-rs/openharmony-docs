# CallAttributeOptions（系统接口）

调用属性选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-export interface CallAttributeOptions--><!--Device-call-export interface CallAttributeOptions-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## accountId

```TypeScript
accountId: int
```

帐户Id。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-accountId: int--><!--Device-CallAttributeOptions-accountId: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## accountNumber

```TypeScript
accountNumber: string
```

账号号码。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-accountNumber: string--><!--Device-CallAttributeOptions-accountNumber: string-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## callId

```TypeScript
callId: int
```

呼叫Id。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-callId: int--><!--Device-CallAttributeOptions-callId: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## callState

```TypeScript
callState: DetailedCallState
```

详细呼叫状态。

**类型：** [DetailedCallState](arkts-telephony-call-detailedcallstate-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-callState: DetailedCallState--><!--Device-CallAttributeOptions-callState: DetailedCallState-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## callType

```TypeScript
callType: CallType
```

通话类型。

**类型：** [CallType](arkts-telephony-call-calltype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-callType: CallType--><!--Device-CallAttributeOptions-callType: CallType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## conferenceState

```TypeScript
conferenceState: ConferenceState
```

会议状态。

**类型：** [ConferenceState](arkts-telephony-call-conferencestate-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-conferenceState: ConferenceState--><!--Device-CallAttributeOptions-conferenceState: ConferenceState-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## crsType

```TypeScript
crsType: int
```

视频彩振类型。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-crsType: int--><!--Device-CallAttributeOptions-crsType: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## extraParams

```TypeScript
extraParams?: Record<string, Object>
```

Indicates the extra call parameters.

**类型：** Record&lt;string, Object&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-extraParams?: Record<string, Object>--><!--Device-CallAttributeOptions-extraParams?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isCustomAccessibility

```TypeScript
isCustomAccessibility?: boolean
```

应用是否支持自定义无障碍能力，默认为false。 -true:支持 -false:不支持 **起始版本:** 26.0.0

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-CallAttributeOptions-isCustomAccessibility?: boolean--><!--Device-CallAttributeOptions-isCustomAccessibility?: boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isEcc

```TypeScript
isEcc: boolean
```

判断是否是Ecc，默认false。 -true：是 -false：否

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-isEcc: boolean--><!--Device-CallAttributeOptions-isEcc: boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## numberLocation

```TypeScript
numberLocation?: string
```

号码归属地信息

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-numberLocation?: string--><!--Device-CallAttributeOptions-numberLocation?: string-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## numberMarkInfo

```TypeScript
numberMarkInfo?: NumberMarkInfo
```

号码标记信息。

**类型：** [NumberMarkInfo](arkts-telephony-call-numbermarkinfo-i-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-numberMarkInfo?: NumberMarkInfo--><!--Device-CallAttributeOptions-numberMarkInfo?: NumberMarkInfo-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## originalCallType

```TypeScript
originalCallType: int
```

视频彩振原始呼叫类型。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-originalCallType: int--><!--Device-CallAttributeOptions-originalCallType: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## rttState

```TypeScript
rttState?: RttState
```

rtt通话状态

**类型：** [RttState](arkts-telephony-call-rttstate-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-rttState?: RttState--><!--Device-CallAttributeOptions-rttState?: RttState-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## speakerphoneOn

```TypeScript
speakerphoneOn: boolean
```

判断是否是扬声器接通电话，默认false。 -true：是 -false：否

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-speakerphoneOn: boolean--><!--Device-CallAttributeOptions-speakerphoneOn: boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: int
```

开始时间。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-startTime: int--><!--Device-CallAttributeOptions-startTime: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## videoState

```TypeScript
videoState: VideoStateType
```

视频状态类型。

**类型：** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-videoState: VideoStateType--><!--Device-CallAttributeOptions-videoState: VideoStateType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## voipCallAttribute

```TypeScript
voipCallAttribute?: VoipCallAttribute
```

VoIP通话信息。

**类型：** [VoipCallAttribute](arkts-telephony-call-voipcallattribute-i-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallAttributeOptions-voipCallAttribute?: VoipCallAttribute--><!--Device-CallAttributeOptions-voipCallAttribute?: VoipCallAttribute-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## xCallType

```TypeScript
xCallType?: XCallType
```

XCALL类型。 **起始版本:** 26.0.0

**类型：** [XCallType](arkts-telephony-call-xcalltype-e-sys.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-CallAttributeOptions-xCallType?: XCallType--><!--Device-CallAttributeOptions-xCallType?: XCallType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

