# GattWriteType

枚举，写入特征值的方式（不同的取值，对端蓝牙设备的表现不一样）。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## WRITE

```TypeScript
WRITE = 1
```

写入特征值后，对端蓝牙设备需要回复确认。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## WRITE_NO_RESPONSE

```TypeScript
WRITE_NO_RESPONSE = 2
```

写入特征值后，对端蓝牙设备不需要回复。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
