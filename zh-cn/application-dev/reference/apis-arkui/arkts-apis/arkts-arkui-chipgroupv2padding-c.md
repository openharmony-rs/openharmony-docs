# ChipGroupV2Padding

ChipGroupV2Padding定义了ChipGroupV2的上下内边距，用于控制其整体高度。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipGroupV2PaddingConfig)
```

ChipGroupV2Padding的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | ChipGroupV2PaddingConfig | 是 | 芯片组内边距配置。 |

## bottom

```TypeScript
public bottom: Length
```

ChipGroupV2的下方内边距（不支持百分比）。

默认值：14

单位：vp

值为undefined时，按默认值处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
public top: Length
```

ChipGroupV2的上方内边距（不支持百分比）。

默认值：14

单位：vp

值为undefined时，按默认值处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

