# IccAccountInfo

```TypeScript
export interface IccAccountInfo
```

Defines the ICC account information.

**Since:** 10

<!--Device-sim-export interface IccAccountInfo--><!--Device-sim-export interface IccAccountInfo-End-->

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## operatorName

```TypeScript
operatorName?: string
```

Indicates the operatorName for card.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-IccAccountInfo-operatorName?: string--><!--Device-IccAccountInfo-operatorName?: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## simLabelIndex

```TypeScript
simLabelIndex?: number
```

Indicates the simLabelIndex for card. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-IccAccountInfo-simLabelIndex?: int--><!--Device-IccAccountInfo-simLabelIndex?: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
