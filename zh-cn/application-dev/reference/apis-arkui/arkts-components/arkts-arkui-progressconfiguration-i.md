# ProgressConfiguration

进度条配置。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。

**继承/实现关系：** ProgressConfiguration extends [CommonConfiguration<ProgressConfiguration>](CommonConfiguration<ProgressConfiguration>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total: number
```

进度总长。

默认值：100

**说明：**

total是负数时，按照100处理。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

当前进度值。当设置的数值小于0时，将其置为0。当设置的数值大于total时，将其置为total。

默认值：0

取值范围：[0, total]

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

