# CallSessionEvent (System API)

```TypeScript
export interface CallSessionEvent
```

Defines the video call event information.

**Since:** 11

<!--Device-call-export interface CallSessionEvent--><!--Device-call-export interface CallSessionEvent-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## callId

```TypeScript
callId: number
```

Call ID.

**Type:** number

**Since:** 11

<!--Device-CallSessionEvent-callId: int--><!--Device-CallSessionEvent-callId: int-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## eventId

```TypeScript
eventId: CallSessionEventId
```

Video call event.

**Type:** [CallSessionEventId](arkts-telephony-call-callsessioneventid-e-sys.md)

**Since:** 11

<!--Device-CallSessionEvent-eventId: CallSessionEventId--><!--Device-CallSessionEvent-eventId: CallSessionEventId-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
