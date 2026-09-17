# DialOptions

Provides an option for determining whether a call is a video call.

**Since:** 6

**System capability:** SystemCapability.Telephony.CallManager

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## accountId

```TypeScript
accountId?: number
```

Account ID.

- **0**: card slot 1.  
- **1**: card slot 2.&lt;br

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## dialScene

```TypeScript
dialScene?: DialScene
```

Dialup scenario. This is a system API.

**Type:** [DialScene](arkts-telephony-call-dialscene-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## dialType

```TypeScript
dialType?: DialType
```

Dialup type. This is a system API.

**Type:** [DialType](arkts-telephony-call-dialtype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## videoState

```TypeScript
videoState?: VideoStateType
```

Video state type. This is a system API.

**Type:** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
