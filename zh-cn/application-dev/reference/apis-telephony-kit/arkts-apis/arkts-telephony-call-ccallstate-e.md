# CCallState

运营商通话状态码。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-export enum CCallState--><!--Device-call-export enum CCallState-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_UNKNOWN

```TypeScript
CCALL_STATE_UNKNOWN = -1
```

无效状态，当获取呼叫状态失败时返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_UNKNOWN = -1--><!--Device-CCallState-CCALL_STATE_UNKNOWN = -1-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_ACTIVE

```TypeScript
CCALL_STATE_ACTIVE = 0
```

表示当前通话已经接通成功。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_ACTIVE = 0--><!--Device-CCallState-CCALL_STATE_ACTIVE = 0-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_HOLDING

```TypeScript
CCALL_STATE_HOLDING = 1
```

表示当前通话处于保持状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_HOLDING = 1--><!--Device-CCallState-CCALL_STATE_HOLDING = 1-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_DIALING

```TypeScript
CCALL_STATE_DIALING = 2
```

表示去电处于拨号过程中，对端还没有收到振铃期间。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_DIALING = 2--><!--Device-CCallState-CCALL_STATE_DIALING = 2-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_ALERTING

```TypeScript
CCALL_STATE_ALERTING = 3
```

表示去电处于振铃过程中，对端处于响铃阶段。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_ALERTING = 3--><!--Device-CCallState-CCALL_STATE_ALERTING = 3-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_INCOMING

```TypeScript
CCALL_STATE_INCOMING = 4
```

表示收到来电。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_INCOMING = 4--><!--Device-CCallState-CCALL_STATE_INCOMING = 4-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_WAITING

```TypeScript
CCALL_STATE_WAITING = 5
```

同一个卡槽上已经存在一路通话的情况下，又收到一路来电。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_WAITING = 5--><!--Device-CCallState-CCALL_STATE_WAITING = 5-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_DISCONNECTED

```TypeScript
CCALL_STATE_DISCONNECTED = 6
```

表示通话已经释放完成。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_DISCONNECTED = 6--><!--Device-CCallState-CCALL_STATE_DISCONNECTED = 6-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_DISCONNECTING

```TypeScript
CCALL_STATE_DISCONNECTING = 7
```

表示通话正在释放中，还没有释放完成。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_DISCONNECTING = 7--><!--Device-CCallState-CCALL_STATE_DISCONNECTING = 7-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_IDLE

```TypeScript
CCALL_STATE_IDLE = 8
```

表示没有正在进行的呼叫。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_IDLE = 8--><!--Device-CCallState-CCALL_STATE_IDLE = 8-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## CCALL_STATE_ANSWERED

```TypeScript
CCALL_STATE_ANSWERED = 9
```

表示来电已经接听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CCallState-CCALL_STATE_ANSWERED = 9--><!--Device-CCallState-CCALL_STATE_ANSWERED = 9-End-->

**系统能力：** SystemCapability.Telephony.CallManager

