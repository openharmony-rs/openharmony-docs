# NrCellInformation (System API)

```TypeScript
export interface NrCellInformation
```

Obtains NR cell information.

**Since:** 8

<!--Device-radio-export interface NrCellInformation--><!--Device-radio-export interface NrCellInformation-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**Type:** string

**Since:** 8

<!--Device-NrCellInformation-mcc: string--><!--Device-NrCellInformation-mcc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**Type:** string

**Since:** 8

<!--Device-NrCellInformation-mnc: string--><!--Device-NrCellInformation-mnc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## nci

```TypeScript
nci: number
```

Indicates the 5G network cell ID.

**Type:** number

**Since:** 8

<!--Device-NrCellInformation-nci: int--><!--Device-NrCellInformation-nci: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## nrArfcn

```TypeScript
nrArfcn: number
```

Indicates the NR-ARFCN(NR Absolute Radio Frequency Channel Number).

**Type:** number

**Since:** 8

<!--Device-NrCellInformation-nrArfcn: int--><!--Device-NrCellInformation-nrArfcn: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## pci

```TypeScript
pci: number
```

Indicates the physical cell identification.

**Type:** number

**Since:** 8

<!--Device-NrCellInformation-pci: int--><!--Device-NrCellInformation-pci: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## tac

```TypeScript
tac: number
```

Indicates the tracking area code.

**Type:** number

**Since:** 8

<!--Device-NrCellInformation-tac: int--><!--Device-NrCellInformation-tac: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
