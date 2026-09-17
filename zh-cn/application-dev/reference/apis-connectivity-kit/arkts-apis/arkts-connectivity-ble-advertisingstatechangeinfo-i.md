# AdvertisingStateChangeInfo

描述BLE广播启动、停止的状态信息。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## advertisingId

```TypeScript
advertisingId: number
```

首次启动广播时会分配该值，后续用于标识当前操作的广播。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: AdvertisingState
```

操作广播后，收到的BLE广播状态。

**类型：** [AdvertisingState](arkts-connectivity-ble-advertisingstate-e.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
