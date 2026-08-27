# CellInformation

小区信息。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
```

## data

```TypeScript
data: CdmaCellInformation | GsmCellInformation | LteCellInformation | NrCellInformation | TdscdmaCellInformation
      | WcdmaCellInformation
```

Obtains signal strength under different network formats.

**类型：** [CdmaCellInformation](arkts-telephony-radio-cdmacellinformation-i-sys.md) \| [GsmCellInformation](arkts-telephony-radio-gsmcellinformation-i-sys.md) \| [LteCellInformation](arkts-telephony-radio-ltecellinformation-i-sys.md) \| [NrCellInformation](arkts-telephony-radio-nrcellinformation-i-sys.md) \| [TdscdmaCellInformation](arkts-telephony-radio-tdscdmacellinformation-i-sys.md) \| [WcdmaCellInformation](arkts-telephony-radio-wcdmacellinformation-i-sys.md)

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## isCamped

```TypeScript
isCamped: boolean
```

Obtains the camp-on status of the serving cell.Returns {@code true} if the user equipment (UE) is camped on the cell; returns {@code false} otherwise.

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## timeStamp

```TypeScript
timeStamp: number
```

Obtains the timestamp when the cell information is obtained.Returns a timestamp since boot, in nanoseconds.

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
