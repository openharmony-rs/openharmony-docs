# CellInformation

Defines the cell information.

**Since:** 8

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## data

```TypeScript
data: CdmaCellInformation | GsmCellInformation | LteCellInformation | NrCellInformation | TdscdmaCellInformation
      | WcdmaCellInformation
```

Obtains signal strength under different network formats.

**Type:** [CdmaCellInformation](arkts-telephony-radio-cdmacellinformation-i-sys.md) &#124; [GsmCellInformation](arkts-telephony-radio-gsmcellinformation-i-sys.md) &#124; [LteCellInformation](arkts-telephony-radio-ltecellinformation-i-sys.md) &#124; [NrCellInformation](arkts-telephony-radio-nrcellinformation-i-sys.md) &#124; [TdscdmaCellInformation](arkts-telephony-radio-tdscdmacellinformation-i-sys.md) &#124; [WcdmaCellInformation](arkts-telephony-radio-wcdmacellinformation-i-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## isCamped

```TypeScript
isCamped: boolean
```

Obtains the camp-on status of the serving cell.

Returns `true` if the user equipment (UE) is camped on the cell; returns `false` otherwise.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## timeStamp

```TypeScript
timeStamp: number
```

Obtains the timestamp when the cell information is obtained.

Returns a timestamp since boot, in nanoseconds.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
