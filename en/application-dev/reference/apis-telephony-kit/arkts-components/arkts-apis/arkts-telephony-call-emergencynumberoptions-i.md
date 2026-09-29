# EmergencyNumberOptions

```TypeScript
export interface EmergencyNumberOptions
```

Provides an option for determining whether a number is an emergency number for the SIM card in the specified slot.

**Since:** 7

<!--Device-call-export interface EmergencyNumberOptions--><!--Device-call-export interface EmergencyNumberOptions-End-->

**System capability:** SystemCapability.Telephony.CallManager

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## slotId

```TypeScript
slotId?: number
```

Card slot ID.

- **0**: card slot 1  
- **1**: card slot 2

**Type:** number

**Since:** 7

<!--Device-EmergencyNumberOptions-slotId?: int--><!--Device-EmergencyNumberOptions-slotId?: int-End-->

**System capability:** SystemCapability.Telephony.CallManager
