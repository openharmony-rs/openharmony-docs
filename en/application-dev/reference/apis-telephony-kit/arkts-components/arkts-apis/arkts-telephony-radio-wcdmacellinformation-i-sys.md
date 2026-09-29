# WcdmaCellInformation (System API)

```TypeScript
export interface WcdmaCellInformation
```

Obtains WCDMA cell information.

**Since:** 8

<!--Device-radio-export interface WcdmaCellInformation--><!--Device-radio-export interface WcdmaCellInformation-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## cellId

```TypeScript
cellId: number
```

Indicates the cell ID.

**Type:** number

**Since:** 8

<!--Device-WcdmaCellInformation-cellId: int--><!--Device-WcdmaCellInformation-cellId: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## lac

```TypeScript
lac: number
```

Indicates the location area code.

**Type:** number

**Since:** 8

<!--Device-WcdmaCellInformation-lac: int--><!--Device-WcdmaCellInformation-lac: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**Type:** string

**Since:** 8

<!--Device-WcdmaCellInformation-mcc: string--><!--Device-WcdmaCellInformation-mcc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**Type:** string

**Since:** 8

<!--Device-WcdmaCellInformation-mnc: string--><!--Device-WcdmaCellInformation-mnc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## psc

```TypeScript
psc: number
```

Indicates the primary scrambling code.

**Type:** number

**Since:** 8

<!--Device-WcdmaCellInformation-psc: int--><!--Device-WcdmaCellInformation-psc: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## uarfcn

```TypeScript
uarfcn: number
```

Indicates the absolute radio frequency number.

**Type:** number

**Since:** 8

<!--Device-WcdmaCellInformation-uarfcn: int--><!--Device-WcdmaCellInformation-uarfcn: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
