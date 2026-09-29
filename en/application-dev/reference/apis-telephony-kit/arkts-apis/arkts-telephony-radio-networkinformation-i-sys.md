# NetworkInformation (System API)

```TypeScript
export interface NetworkInformation
```

Obtains the network information.

**Since:** 6

<!--Device-radio-export interface NetworkInformation--><!--Device-radio-export interface NetworkInformation-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## operatorName

```TypeScript
operatorName: string
```

Indicates the name of the operator.

**Type:** string

**Since:** 6

<!--Device-NetworkInformation-operatorName: string--><!--Device-NetworkInformation-operatorName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## operatorNumeric

```TypeScript
operatorNumeric: string
```

Indicates the number of the operator.

**Type:** string

**Since:** 6

<!--Device-NetworkInformation-operatorNumeric: string--><!--Device-NetworkInformation-operatorNumeric: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## radioTech

```TypeScript
radioTech: string
```

Indicates the radio Technology.

**Type:** string

**Since:** 6

<!--Device-NetworkInformation-radioTech: string--><!--Device-NetworkInformation-radioTech: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## state

```TypeScript
state: NetworkInformationState
```

Indicates the status of network information.

**Type:** [NetworkInformationState](arkts-telephony-radio-networkinformationstate-e-sys.md)

**Since:** 6

<!--Device-NetworkInformation-state: NetworkInformationState--><!--Device-NetworkInformation-state: NetworkInformationState-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
