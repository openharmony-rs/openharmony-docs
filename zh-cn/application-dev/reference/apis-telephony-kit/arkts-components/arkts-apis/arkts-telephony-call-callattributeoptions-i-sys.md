# CallAttributeOptions（系统接口）

调用属性选项。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## accountId

```TypeScript
accountId: number
```

帐户Id。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## accountNumber

```TypeScript
accountNumber: string
```

账号号码。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## callId

```TypeScript
callId: number
```

呼叫Id。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## callState

```TypeScript
callState: DetailedCallState
```

详细呼叫状态。

**类型：** [DetailedCallState](arkts-telephony-call-detailedcallstate-e-sys.md)

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## callType

```TypeScript
callType: CallType
```

通话类型。

**类型：** [CallType](arkts-telephony-call-calltype-e-sys.md)

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## conferenceState

```TypeScript
conferenceState: ConferenceState
```

会议状态。

**类型：** [ConferenceState](arkts-telephony-call-conferencestate-e-sys.md)

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## crsType

```TypeScript
crsType: number
```

视频彩振类型。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## extraParams

```TypeScript
extraParams?: Record<string, Object>
```

Indicates the extra call parameters.

**类型：** Record&lt;string, Object&gt;

**起始版本：** 14

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isCustomAccessibility

```TypeScript
isCustomAccessibility?: boolean
```

应用是否支持自定义无障碍能力，默认为false。

-true:支持

-false:不支持

**起始版本:** 26.0.0

**类型：** boolean

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isEcc

```TypeScript
isEcc: boolean
```

判断是否是Ecc，默认false。

-true：是

-false：否

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## numberLocation

```TypeScript
numberLocation?: string
```

号码归属地信息

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## numberMarkInfo

```TypeScript
numberMarkInfo?: NumberMarkInfo
```

号码标记信息。

**类型：** [NumberMarkInfo](arkts-telephony-call-numbermarkinfo-i-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## originalCallType

```TypeScript
originalCallType: number
```

视频彩振原始呼叫类型。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## rttState

```TypeScript
rttState?: RttState
```

rtt通话状态

**类型：** [RttState](arkts-telephony-call-rttstate-e-sys.md)

**起始版本：** 22

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## speakerphoneOn

```TypeScript
speakerphoneOn: boolean
```

判断是否是扬声器接通电话，默认false。

-true：是

-false：否

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: number
```

开始时间。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## videoState

```TypeScript
videoState: VideoStateType
```

视频状态类型。

**类型：** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## voipCallAttribute

```TypeScript
voipCallAttribute?: VoipCallAttribute
```

VoIP通话信息。

**类型：** [VoipCallAttribute](arkts-telephony-call-voipcallattribute-i-sys.md)

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## xCallType

```TypeScript
xCallType?: XCallType
```

XCALL类型。

**起始版本:** 26.0.0

**类型：** [XCallType](arkts-telephony-call-xcalltype-e-sys.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。
