# LocalizedLabelMarginOptions

LocalizedLabelMarginOptions用于定义本地化文本与左右侧图标之间间距。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: LengthMetrics
```

文本与右侧图标之间间距，不支持百分比。

默认值：

size为ChipSize.SMALL时，end默认值：

`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`

size为ChipSize.NORMAL时，end默认值:

`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`

值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: LengthMetrics
```

文本与左侧图标之间间距，不支持百分比。

默认值：

size为ChipSize.SMALL时，start默认值:

`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`

size为ChipSize.NORMAL时，start默认值：

`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`

值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

