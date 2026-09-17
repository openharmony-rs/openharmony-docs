# ConnectionParam

枚举，连接参数类型。

**起始版本：** 22

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## LOW_POWER

```TypeScript
LOW_POWER = 1
```

低功耗模式，传输数据速度慢，但功耗少。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## BALANCED

```TypeScript
BALANCED = 2
```

均衡模式，平衡延迟和功耗，如果没有请求连接参数更新，这是默认值。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## HIGH

```TypeScript
HIGH = 3
```

高速率模式，传输数据速度快，但功耗多。

当需要快速传输大量数据时应采用该连接参数，传输完成后，应请求BALANCED连接参数，以减少功耗。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
