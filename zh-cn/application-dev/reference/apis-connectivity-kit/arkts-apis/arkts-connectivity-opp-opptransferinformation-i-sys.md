# OppTransferInformation（系统接口）

描述文件的传输信息。

**起始版本：** 16

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## currentBytes

```TypeScript
currentBytes: number
```

当前传输的字节数。

**类型：** number

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## currentCount

```TypeScript
currentCount: number
```

本次传输当前文件序列。

**类型：** number

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## direction

```TypeScript
direction: DirectionType
```

传输方向。

**类型：** [DirectionType](arkts-connectivity-opp-directiontype-e-sys.md)

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## filePath

```TypeScript
filePath: string
```

待传输文件的URI，例如：file://media/Photo/1/IMG_1739266559_000/test.jpg 。

**类型：** string

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**测试接口：** 此接口仅在自动化测试脚本中使用。

## remoteDeviceId

```TypeScript
remoteDeviceId: string
```

传输对端MAC地址。

**类型：** string

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## remoteDeviceName

```TypeScript
remoteDeviceName: string
```

传输对端设备名。

**类型：** string

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result: TransferResult
```

传输结果。

**类型：** [TransferResult](arkts-connectivity-opp-transferresult-e-sys.md)

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: TransferStatus
```

传输状态。

**类型：** [TransferStatus](arkts-connectivity-opp-transferstatus-e-sys.md)

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## totalBytes

```TypeScript
totalBytes: number
```

需要传输的总字节数。

**类型：** number

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## totalCount

```TypeScript
totalCount: number
```

本次传输总传输的文件个数。

**类型：** number

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
