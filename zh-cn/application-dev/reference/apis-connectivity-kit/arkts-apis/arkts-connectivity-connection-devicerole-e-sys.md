# DeviceRole（系统接口）

枚举，蓝牙设备在连接过程中的角色。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## DEVICE_ROLE_PERIPHERAL_ONLY

```TypeScript
DEVICE_ROLE_PERIPHERAL_ONLY = 0
```

表示该蓝牙设备仅支持作为外围设备。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## DEVICE_ROLE_CENTRAL_ONLY

```TypeScript
DEVICE_ROLE_CENTRAL_ONLY = 1
```

表示该蓝牙设备仅支持作为中心设备。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## DEVICE_ROLE_BOTH_PREFER_PERIPHERAL

```TypeScript
DEVICE_ROLE_BOTH_PREFER_PERIPHERAL = 2
```

表示该蓝牙设备既可以作为中心设备，也可以作为外围设备，但优先作为外围设备。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## DEVICE_ROLE_BOTH_PREFER_CENTRAL

```TypeScript
DEVICE_ROLE_BOTH_PREFER_CENTRAL = 3
```

表示该蓝牙设备既可以作为中心设备，也可以作为外围设备，但优先作为中心设备。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
