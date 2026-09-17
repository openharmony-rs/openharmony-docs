# GattSetting

描述GATT连接的参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## autoConnect

```TypeScript
autoConnect?: boolean
```

是否直接连接到远端设备或者在远端设备可用时自动连接。true表示在远端设备可用时自动连接，false表示直接连接到远端设备。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## transport

```TypeScript
transport?: BluetoothTransport
```

连接的传输类型，默认值为TRANSPORT_LE。

**类型：** [BluetoothTransport](arkts-connectivity-ble-bluetoothtransport-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
