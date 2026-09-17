# AdvertisingDisableParams

停止指定标识的BLE广播时设置的参数。

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

需要停止的广播标识。该值由[ble.startAdvertising](arkts-connectivity-ble-startadvertising-f.md)首次启动广播时分配。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
