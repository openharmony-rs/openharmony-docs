# ChipGroupV2ItemStyle

ChipGroupV2ItemStyle定义了ChipV2的共通属性类。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipGroupV2ItemStyleConfig)
```

ChipGroupV2ItemStyle的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | ChipGroupV2ItemStyleConfig | 是 | 芯片组项样式配置。 |

## backgroundColor

```TypeScript
public backgroundColor?: ColorMetrics
```

ChipV2背景颜色。

默认值：$r('sys.color.ohos_id_color_button_normal')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
public backgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜色
[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影
[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)效果、材质层滤镜效果
[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter-1)。

默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
public fontColor?: ColorMetrics
```

ChipV2文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
public selectedBackgroundColor?: ColorMetrics
```

ChipV2激活时的背景颜色。

默认值：$r('sys.color.ohos_id_color_emphasize')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundSystemMaterial

```TypeScript
public selectedBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件选中状态下的系统材质样式。不同材质具有不同的效果，能够影响组件的背景色
[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜色
[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影
[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)效果、材质层滤镜效果
[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter-1)。

默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
public selectedFontColor?: ColorMetrics
```

ChipV2激活时的文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary_contrary')

值为undefined时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
public size?: ChipV2Size | SizeT<LengthMetrics>
```

ChipV2尺寸。

默认值：ChipV2Size.NORMAL

值为undefined时，按默认值处理。

**类型：** ChipV2Size | SizeT<LengthMetrics>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

