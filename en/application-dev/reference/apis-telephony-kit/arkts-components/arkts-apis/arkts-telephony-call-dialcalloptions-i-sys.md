# DialCallOptions (System API)

Provides an option for determining whether a call is a video call.

**Since:** 9

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

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
- **1**: card slot 2.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## dialScene

```TypeScript
dialScene?: DialScene
```

Dialup scenario.

**Type:** [DialScene](arkts-telephony-call-dialscene-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## dialType

```TypeScript
dialType?: DialType
```

Dialup type.

**Type:** [DialType](arkts-telephony-call-dialtype-e-sys.md)

**Since:** 9

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

## videoState

```TypeScript
videoState?: VideoStateType
```

Video state type.

**Type:** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## xCallType

```TypeScript
xCallType?: XCallType
```

XCALL type.

**Type:** [XCallType](arkts-telephony-call-xcalltype-e-sys.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
