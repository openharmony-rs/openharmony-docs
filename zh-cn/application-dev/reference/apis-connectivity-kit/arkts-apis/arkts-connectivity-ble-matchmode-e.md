# MatchMode

枚举，硬件过滤匹配模式。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## MATCH_MODE_AGGRESSIVE

```TypeScript
MATCH_MODE_AGGRESSIVE = 1
```

当广播报文信号强度较低或者短时间内广播报文的发送次数较少时，可以更快地上报。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## MATCH_MODE_STICKY

```TypeScript
MATCH_MODE_STICKY = 2
```

广播报文信号强度较高或者短时间内广播报文的发送次数较多时，才会上报。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
