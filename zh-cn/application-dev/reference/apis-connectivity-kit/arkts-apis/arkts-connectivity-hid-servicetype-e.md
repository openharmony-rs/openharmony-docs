# ServiceType

枚举，描述HID设备与主机之间连接的服务类型。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## SERVICE_NO_TRAFFIC

```TypeScript
SERVICE_NO_TRAFFIC = 0
```

低功耗模式，仅维持连接，不传输应用数据，功耗最低。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## SERVICE_BEST_EFFORT

```TypeScript
SERVICE_BEST_EFFORT = 1
```

高速模式，传输速率最快，但是数据包可能丢失或乱序，适用于对延迟敏感但对丢包不敏感的场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## SERVICE_GUARANTEED

```TypeScript
SERVICE_GUARANTEED = 2
```

可靠模式，传输速度稍慢，但是保证数据正确送达，适用于文件传输等场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
