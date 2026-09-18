# BLEConnectionChangeState

描述GATT profile协议连接状态。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

对端蓝牙设备地址。例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## reason

```TypeScript
reason?: GattDisconnectReason
```

GATT链路断连原因，仅在连接状态为 [STATE_DISCONNECTED](arkts-connectivity-constant-profileconnectionstate-e.md) 时提供，其他连接状态下断连原因默认为undefined。

**类型：** [GattDisconnectReason](arkts-connectivity-ble-gattdisconnectreason-e.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## reasonMessage

```TypeScript
reasonMessage?: string
```

GATT链路断连原因，仅在连接状态为 [STATE_DISCONNECTED](arkts-connectivity-constant-profileconnectionstate-e.md) 时提供，其他连接状态下断连原因默认为undefined。例如：本端主动断开连接时，返回：0X16_LOCAL_HOST。 **起始版本**：26.0.0

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

GATT profile连接状态。

**类型：** [ProfileConnectionState](arkts-connectivity-ble-profileconnectionstate-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
