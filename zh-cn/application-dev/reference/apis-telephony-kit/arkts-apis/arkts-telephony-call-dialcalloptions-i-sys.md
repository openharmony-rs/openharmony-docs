# DialCallOptions（系统接口）

拨打电话的可选参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-export interface DialCallOptions--><!--Device-call-export interface DialCallOptions-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## accountId

```TypeScript
accountId?: int
```

帐户Id。 - 0：卡槽1。 - 1：卡槽2。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DialCallOptions-accountId?: int--><!--Device-DialCallOptions-accountId?: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## dialScene

```TypeScript
dialScene?: DialScene
```

拨号场景。

**类型：** [DialScene](arkts-telephony-call-dialscene-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DialCallOptions-dialScene?: DialScene--><!--Device-DialCallOptions-dialScene?: DialScene-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## dialType

```TypeScript
dialType?: DialType
```

拨号类型。

**类型：** [DialType](arkts-telephony-call-dialtype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DialCallOptions-dialType?: DialType--><!--Device-DialCallOptions-dialType?: DialType-End-->

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

<!--Device-DialCallOptions-extraParams?: Record<string, Object>--><!--Device-DialCallOptions-extraParams?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## videoState

```TypeScript
videoState?: VideoStateType
```

视频状态类型。

**类型：** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DialCallOptions-videoState?: VideoStateType--><!--Device-DialCallOptions-videoState?: VideoStateType-End-->

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

<!--Device-DialCallOptions-xCallType?: XCallType--><!--Device-DialCallOptions-xCallType?: XCallType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

