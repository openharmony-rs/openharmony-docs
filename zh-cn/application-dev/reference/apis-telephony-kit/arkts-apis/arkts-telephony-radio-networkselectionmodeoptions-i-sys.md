# NetworkSelectionModeOptions（系统接口）

Obtains the network selection mode option.

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## networkInformation

```TypeScript
networkInformation: NetworkInformation
```

Indicates the network information.

**类型：** [NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md)

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## resumeSelection

```TypeScript
resumeSelection: boolean
```

Indicates whether to continue selecting the network selection mode.

**类型：** boolean

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## selectMode

```TypeScript
selectMode: NetworkSelectionMode
```

Indicates the network search mode of the SIM card.

**类型：** [NetworkSelectionMode](arkts-telephony-radio-networkselectionmode-e.md)

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## slotId

```TypeScript
slotId: number
```

Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device.

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
