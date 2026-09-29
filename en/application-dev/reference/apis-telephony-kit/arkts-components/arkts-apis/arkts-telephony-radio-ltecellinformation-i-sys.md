# LteCellInformation (System API)

```TypeScript
export interface LteCellInformation
```

Obtains LTE cell information.

**Since:** 8

<!--Device-radio-export interface LteCellInformation--><!--Device-radio-export interface LteCellInformation-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## bandwidth

```TypeScript
bandwidth: number
```

Indicates the bandwidth.

**Type:** number

**Since:** 8

<!--Device-LteCellInformation-bandwidth: int--><!--Device-LteCellInformation-bandwidth: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## cgi

```TypeScript
cgi: number
```

Indicates the cell global identification.

**Type:** number

**Since:** 8

<!--Device-LteCellInformation-cgi: long--><!--Device-LteCellInformation-cgi: long-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## earfcn

```TypeScript
earfcn: number
```

Indicates the E-UTRA Absolute Radio Frequency Channel Number.

**Type:** number

**Since:** 8

<!--Device-LteCellInformation-earfcn: int--><!--Device-LteCellInformation-earfcn: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## isSupportEndc

```TypeScript
isSupportEndc: boolean
```

Support for New Radio_Dual Connectivity.

**Type:** boolean

**Since:** 8

<!--Device-LteCellInformation-isSupportEndc: boolean--><!--Device-LteCellInformation-isSupportEndc: boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**Type:** string

**Since:** 8

<!--Device-LteCellInformation-mcc: string--><!--Device-LteCellInformation-mcc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**Type:** string

**Since:** 8

<!--Device-LteCellInformation-mnc: string--><!--Device-LteCellInformation-mnc: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## pci

```TypeScript
pci: number
```

Indicates the physical cell identification.

**Type:** number

**Since:** 8

<!--Device-LteCellInformation-pci: int--><!--Device-LteCellInformation-pci: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## tac

```TypeScript
tac: number
```

Indicates the tracking area code.

**Type:** number

**Since:** 8

<!--Device-LteCellInformation-tac: int--><!--Device-LteCellInformation-tac: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
