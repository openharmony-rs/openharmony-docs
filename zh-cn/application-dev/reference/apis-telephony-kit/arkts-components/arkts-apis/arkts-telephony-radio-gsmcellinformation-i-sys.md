# GsmCellInformation（系统接口）

```TypeScript
export interface GsmCellInformation
```

Obtains GSM cell information.

**起始版本：** 8

<!--Device-radio-export interface GsmCellInformation--><!--Device-radio-export interface GsmCellInformation-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## arfcn

```TypeScript
arfcn: number
```

Indicates the ARFCN(absolute radio frequency channel int).

**类型：** number

**起始版本：** 8

<!--Device-GsmCellInformation-arfcn: int--><!--Device-GsmCellInformation-arfcn: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## bsic

```TypeScript
bsic: number
```

Indicates the base station identification code.

**类型：** number

**起始版本：** 8

<!--Device-GsmCellInformation-bsic: int--><!--Device-GsmCellInformation-bsic: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## cellId

```TypeScript
cellId: number
```

Indicates the cell identification.

**类型：** number

**起始版本：** 8

<!--Device-GsmCellInformation-cellId: int--><!--Device-GsmCellInformation-cellId: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## lac

```TypeScript
lac: number
```

Indicates the location area code.

**类型：** number

**起始版本：** 8

<!--Device-GsmCellInformation-lac: int--><!--Device-GsmCellInformation-lac: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**类型：** string

**起始版本：** 8

<!--Device-GsmCellInformation-mcc: string--><!--Device-GsmCellInformation-mcc: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**类型：** string

**起始版本：** 8

<!--Device-GsmCellInformation-mnc: string--><!--Device-GsmCellInformation-mnc: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
