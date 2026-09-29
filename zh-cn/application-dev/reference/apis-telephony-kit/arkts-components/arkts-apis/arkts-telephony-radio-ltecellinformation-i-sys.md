# LteCellInformation（系统接口）

```TypeScript
export interface LteCellInformation
```

Obtains LTE cell information.

**起始版本：** 8

<!--Device-radio-export interface LteCellInformation--><!--Device-radio-export interface LteCellInformation-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## bandwidth

```TypeScript
bandwidth: number
```

Indicates the bandwidth.

**类型：** number

**起始版本：** 8

<!--Device-LteCellInformation-bandwidth: int--><!--Device-LteCellInformation-bandwidth: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## cgi

```TypeScript
cgi: number
```

Indicates the cell global identification.

**类型：** number

**起始版本：** 8

<!--Device-LteCellInformation-cgi: long--><!--Device-LteCellInformation-cgi: long-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## earfcn

```TypeScript
earfcn: number
```

Indicates the E-UTRA Absolute Radio Frequency Channel Number.

**类型：** number

**起始版本：** 8

<!--Device-LteCellInformation-earfcn: int--><!--Device-LteCellInformation-earfcn: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## isSupportEndc

```TypeScript
isSupportEndc: boolean
```

Support for New Radio_Dual Connectivity.

**类型：** boolean

**起始版本：** 8

<!--Device-LteCellInformation-isSupportEndc: boolean--><!--Device-LteCellInformation-isSupportEndc: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## mcc

```TypeScript
mcc: string
```

Indicates the mobile country code.

**类型：** string

**起始版本：** 8

<!--Device-LteCellInformation-mcc: string--><!--Device-LteCellInformation-mcc: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## mnc

```TypeScript
mnc: string
```

Indicates the mobile network code.

**类型：** string

**起始版本：** 8

<!--Device-LteCellInformation-mnc: string--><!--Device-LteCellInformation-mnc: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## pci

```TypeScript
pci: number
```

Indicates the physical cell identification.

**类型：** number

**起始版本：** 8

<!--Device-LteCellInformation-pci: int--><!--Device-LteCellInformation-pci: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## tac

```TypeScript
tac: number
```

Indicates the tracking area code.

**类型：** number

**起始版本：** 8

<!--Device-LteCellInformation-tac: int--><!--Device-LteCellInformation-tac: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
