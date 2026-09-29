# TrustedPairedDevice（系统接口）

```TypeScript
interface TrustedPairedDevice
```

云设备信息。

**起始版本：** 15

<!--Device-connection-interface TrustedPairedDevice--><!--Device-connection-interface TrustedPairedDevice-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## bluetoothClass

```TypeScript
bluetoothClass: number
```

表示远端设备类型。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-bluetoothClass: int--><!--Device-TrustedPairedDevice-bluetoothClass: int-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName: string
```

表示设备名字。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-deviceName: string--><!--Device-TrustedPairedDevice-deviceName: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceNameTime

```TypeScript
deviceNameTime: number
```

表示设备名字的修改时间。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-deviceNameTime: long--><!--Device-TrustedPairedDevice-deviceNameTime: long-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceType

```TypeScript
deviceType: string
```

表示设备类型。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-deviceType: string--><!--Device-TrustedPairedDevice-deviceType: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## hiLinkVersion

```TypeScript
hiLinkVersion: string
```

表示hilink版本信息。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-hiLinkVersion: string--><!--Device-TrustedPairedDevice-hiLinkVersion: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## macAddress

```TypeScript
macAddress: string
```

表示设备MAC地址。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-macAddress: string--><!--Device-TrustedPairedDevice-macAddress: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## manufactory

```TypeScript
manufactory: string
```

表示制造商信息。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-manufactory: string--><!--Device-TrustedPairedDevice-manufactory: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## modelId

```TypeScript
modelId: string
```

表示左侧耳机的充电状态。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-modelId: string--><!--Device-TrustedPairedDevice-modelId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## pairState

```TypeScript
pairState: number
```

表示设备配对状态。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-pairState: int--><!--Device-TrustedPairedDevice-pairState: int-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## productId

```TypeScript
productId: string
```

表示设备产品信息。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-productId: string--><!--Device-TrustedPairedDevice-productId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## secureAdvertisingInfo

```TypeScript
secureAdvertisingInfo: ArrayBuffer
```

表示设备广播信息。

**类型：** ArrayBuffer

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-secureAdvertisingInfo: ArrayBuffer--><!--Device-TrustedPairedDevice-secureAdvertisingInfo: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## serviceId

```TypeScript
serviceId: string
```

表示设备ID。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-serviceId: string--><!--Device-TrustedPairedDevice-serviceId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## serviceType

```TypeScript
serviceType: string
```

表示设备服务类型。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-serviceType: string--><!--Device-TrustedPairedDevice-serviceType: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## sn

```TypeScript
sn: string
```

表示设备的序列号。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-sn: string--><!--Device-TrustedPairedDevice-sn: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token: ArrayBuffer
```

表示设备的token信息。

**类型：** ArrayBuffer

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-token: ArrayBuffer--><!--Device-TrustedPairedDevice-token: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## uuids

```TypeScript
uuids: string
```

表示设备的UUID。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevice-uuids: string--><!--Device-TrustedPairedDevice-uuids: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
