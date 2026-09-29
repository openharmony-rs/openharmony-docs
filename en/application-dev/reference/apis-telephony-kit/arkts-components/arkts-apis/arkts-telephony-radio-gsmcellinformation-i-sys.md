# GsmCellInformation (System API)

```TypeScript
export interface GsmCellInformation
```

Obtains GSM cell information.

**Since:** 8

<!--Device-radio-export interface GsmCellInformation--><!--Device-radio-export interface GsmCellInformation-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## arfcn

```TypeScript
arfcn: number
```

Indicates the ARFCN(absolute radio frequency channel int).

**Type:** number

**Since:** 8

<!--Device-GsmCellInformation-arfcn: int--><!--Device-GsmCellInformation-arfcn: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## bsic

```TypeScript
bsic: number
```

Indicates the base station identification code.

**Type:** number

**Since:** 8

<!--Device-GsmCellInformation-bsic: int--><!--Device-GsmCellInformation-bsic: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## cellId

```TypeScript
cellId: number
```

Indicates the cell identification.

**Type:** number

**Since:** 8

<!--Device-GsmCellInformation-cellId: int--><!--Device-GsmCellInformation-cellId: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## lac

```TypeScript
lac: number
```

Indicates the location area code.

**Type:** number

**Since:** 8

<!--Device-GsmCellInformation-lac: int--><!--Device-GsmCellInformation-lac: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**Type:** string

**Since:** 8

<!--Device-GsmCellInformation-mcc: string--><!--Device-GsmCellInformation-mcc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**Type:** string

**Since:** 8

<!--Device-GsmCellInformation-mnc: string--><!--Device-GsmCellInformation-mnc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
