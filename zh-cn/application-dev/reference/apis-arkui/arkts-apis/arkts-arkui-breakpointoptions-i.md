# BreakpointOptions

定义断点配置选项，用于指定容器尺寸分析的阈值参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Array<number>
```

高度断点值数组，高度断点值是组件高度与宽度的比值。无单位。数组必须为单调递增数组。<br/>默认值：[0.8, 1.2]，与窗口高度断点默认值一致。<br/>**说明：**<br/>最多支持3个断点，即数组最大长度为2。

**类型：** Array<number>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Array<number>
```

宽度断点值数组。数组必须为单调递增数组。<br/>默认值：[320, 600, 840, 1440]，单位vp，与窗口宽度断点默认值一致。<br/>**说明：**<br/>最多可支持5个断点，即数组最大长度为4。

**类型：** Array<number>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

