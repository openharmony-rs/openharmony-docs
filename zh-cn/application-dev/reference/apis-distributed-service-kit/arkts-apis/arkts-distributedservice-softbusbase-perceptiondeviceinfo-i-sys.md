# PerceptionDeviceInfo（系统接口）

```TypeScript
export interface PerceptionDeviceInfo
```

定义感知扫描发现的设备信息，包括设备类型、设备ID、自定义广告中携带的数据。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## customData

```TypeScript
customData: ArrayBuffer
```

广告中携带的自定义数据，为ArrayBuffer格式的二进制数据。长度与发现设备的广告中携带的自定义数据的长度。个字节。最大长度为5。

**类型：** ArrayBuffer

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: ArrayBuffer
```

设备ID，二进制数据，格式为**ArrayBuffer**。长度为6字节。字节。字节是以网络字节序(big-endian)。最大长度为6。

**类型：** ArrayBuffer

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## deviceType

```TypeScript
deviceType: number
```

设备类型。整数形式。具体值以系统定义为准。取值限定为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。
