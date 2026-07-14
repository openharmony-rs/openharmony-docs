# ScanResults

扫描结果的内容。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## address

```TypeScript
address: string
```

远端设备的地址。
长度为17，由十六进制数字和冒号组成，例如：11:22:33:AA:BB:FF。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## data

```TypeScript
data: ArrayBuffer
```

原始数据。

**类型：** ArrayBuffer

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## deviceClass

```TypeScript
deviceClass?: nearlinkConstant.DeviceClass
```

设备类型。

**类型：** nearlinkConstant.DeviceClass

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## deviceName

```TypeScript
deviceName: string
```

外围设备的设备名称。
最大长度为26。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## isConnectable

```TypeScript
isConnectable: boolean
```

广播是否可连接。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## rssi

```TypeScript
rssi: number
```

外围设备的RSSI。
单位为： 分贝毫瓦，取值范围为全体整数，取值为127时表示无效值。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

