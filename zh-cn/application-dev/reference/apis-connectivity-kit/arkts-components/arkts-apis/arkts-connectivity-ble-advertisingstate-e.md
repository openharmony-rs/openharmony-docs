# AdvertisingState

枚举，不同操作对应的BLE广播状态。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## STARTED

```TypeScript
STARTED = 1
```

调用[startAdvertising](arkts-connectivity-ble-startadvertising-f.md)方法后，广播首次启动成功，且会分配相关资源。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## ENABLED

```TypeScript
ENABLED = 2
```

调用[enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md)方法后，广播启动成功。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## DISABLED

```TypeScript
DISABLED = 3
```

调用[disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md)方法后，广播停止成功。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## STOPPED

```TypeScript
STOPPED = 4
```

调用[stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md)方法后，广播停止成功，且会释放首次启动广播时分配的相关资源。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
