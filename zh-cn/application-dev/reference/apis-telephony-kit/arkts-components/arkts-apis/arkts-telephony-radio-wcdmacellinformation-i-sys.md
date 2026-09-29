# WcdmaCellInformation（系统接口）

```TypeScript
export interface WcdmaCellInformation
```

Obtains WCDMA cell information.

**起始版本：** 8

<!--Device-radio-export interface WcdmaCellInformation--><!--Device-radio-export interface WcdmaCellInformation-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## cellId

```TypeScript
cellId: number
```

Indicates the cell ID.

**类型：** number

**起始版本：** 8

<!--Device-WcdmaCellInformation-cellId: int--><!--Device-WcdmaCellInformation-cellId: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## lac

```TypeScript
lac: number
```

Indicates the location area code.

**类型：** number

**起始版本：** 8

<!--Device-WcdmaCellInformation-lac: int--><!--Device-WcdmaCellInformation-lac: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**类型：** string

**起始版本：** 8

<!--Device-WcdmaCellInformation-mcc: string--><!--Device-WcdmaCellInformation-mcc: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**类型：** string

**起始版本：** 8

<!--Device-WcdmaCellInformation-mnc: string--><!--Device-WcdmaCellInformation-mnc: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## psc

```TypeScript
psc: number
```

Indicates the primary scrambling code.

**类型：** number

**起始版本：** 8

<!--Device-WcdmaCellInformation-psc: int--><!--Device-WcdmaCellInformation-psc: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## uarfcn

```TypeScript
uarfcn: number
```

Indicates the absolute radio frequency number.

**类型：** number

**起始版本：** 8

<!--Device-WcdmaCellInformation-uarfcn: int--><!--Device-WcdmaCellInformation-uarfcn: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
