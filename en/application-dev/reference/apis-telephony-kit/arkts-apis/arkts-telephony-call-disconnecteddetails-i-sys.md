# DisconnectedDetails (System API)

```TypeScript
export interface DisconnectedDetails
```

Defines the call disconnection cause.

**Since:** 9

<!--Device-call-export interface DisconnectedDetails--><!--Device-call-export interface DisconnectedDetails-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## message

```TypeScript
message: string
```

Call ending message.

**Type:** string

**Since:** 9

<!--Device-DisconnectedDetails-message: string--><!--Device-DisconnectedDetails-message: string-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## reason

```TypeScript
reason: DisconnectedReason
```

Defines the call disconnection cause.

**Type:** [DisconnectedReason](arkts-telephony-call-disconnectedreason-e-sys.md)

**Since:** 9

<!--Device-DisconnectedDetails-reason: DisconnectedReason--><!--Device-DisconnectedDetails-reason: DisconnectedReason-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
