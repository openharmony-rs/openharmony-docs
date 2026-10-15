# DeviceChargeState

```TypeScript
enum DeviceChargeState
```

枚举，表示设备当前的充电状态。

**起始版本：** 12

<!--Device-connection-enum DeviceChargeState--><!--Device-connection-enum DeviceChargeState-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## DEVICE_NORMAL_CHARGE_IN_CHARGING

```TypeScript
DEVICE_NORMAL_CHARGE_IN_CHARGING = 1
```

不支持超级快充能力的设备当前处于充电状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceChargeState-DEVICE_NORMAL_CHARGE_IN_CHARGING = 1--><!--Device-DeviceChargeState-DEVICE_NORMAL_CHARGE_IN_CHARGING = 1-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## DEVICE_NORMAL_CHARGE_NOT_CHARGED

```TypeScript
DEVICE_NORMAL_CHARGE_NOT_CHARGED = 0
```

不支持超级快充能力的设备当前处于未充电状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceChargeState-DEVICE_NORMAL_CHARGE_NOT_CHARGED = 0--><!--Device-DeviceChargeState-DEVICE_NORMAL_CHARGE_NOT_CHARGED = 0-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## DEVICE_SUPER_CHARGE_IN_CHARGING

```TypeScript
DEVICE_SUPER_CHARGE_IN_CHARGING = 3
```

支持超级快充能力的设备当前处于充电状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceChargeState-DEVICE_SUPER_CHARGE_IN_CHARGING = 3--><!--Device-DeviceChargeState-DEVICE_SUPER_CHARGE_IN_CHARGING = 3-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## DEVICE_SUPER_CHARGE_NOT_CHARGED

```TypeScript
DEVICE_SUPER_CHARGE_NOT_CHARGED = 2
```

支持超级快充能力的设备当前处于未充电状态。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceChargeState-DEVICE_SUPER_CHARGE_NOT_CHARGED = 2--><!--Device-DeviceChargeState-DEVICE_SUPER_CHARGE_NOT_CHARGED = 2-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
