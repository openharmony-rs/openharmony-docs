# AdvertisingEnableParams

启动指定标识的BLE广播时设置的参数。

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

需要启动的广播标识。该值由[ble.startAdvertising](arkts-connectivity-ble-startadvertising-f.md)首次启动广播时分配。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## duration

```TypeScript
duration?: number
```

发送广播的持续时间。取值范围：[1, 65535]，单位：10ms。

如果未指定此参数或者将其设置为0，则会持续发送广播。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
