# CommonSegmentButtonOptions

定义分段按钮组件的可自定义的属性。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

分段按钮组件的背景模糊材质。

值为undefined时，背景模糊材质为BlurStyle.NONE。

**类型：** BlurStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBorderRadius

```TypeScript
backgroundBorderRadius?: LengthMetrics
```

分段按钮整体容器的边框圆角半径。

**说明：**

此属性仅在borderRadiusMode为BorderRadiusMode.CUSTOM时生效。

对于胶囊类多选按钮(type为"capsule"且multiply为true)，此属性不生效，需要用itemBorderRadius配置圆角。

圆角大小受组件尺寸限制，最大值为组件宽或高的一半，不支持百分比设置。

默认值：`$r('sys.float.segmentbutton_container_shape')`

值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

背景板颜色。

默认值：$r('sys.color.ohos_id_color_button_normal')

值为undefined时，按默认值处理。

**类型：** ResourceColor

**默认值：** $r('sys.color.ohos_id_color_button_normal')

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadiusMode

```TypeScript
borderRadiusMode?: BorderRadiusMode
```

边框圆角模式，用于控制圆角计算方式。

默认值：BorderRadiusMode.DEFAULT

值为undefined时，按默认值处理。

**类型：** BorderRadiusMode

**默认值：** BorderRadiusMode.Default

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
buttonPadding?: Padding | Dimension
```

按钮内边距。

默认值：

仅图标按钮和仅文字按钮默认值：`{ top: 4, right: 8, bottom: 4, left: 8 }`

图标+文本按钮默认值：`{ top: 6, right: 8, bottom: 6, left: 8 }`

单位：vp

值为undefined时，按默认值处理。

**类型：** Padding | Dimension

**默认值：** For text only / icon only buttons Padding { top: 4, right: 8, bottom: 4, left: 8 }.
For text & icon buttons Padding { top: 6, right: 8, bottom: 6, left: 8 }.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

分段按钮组件的布局方向。

默认值：Direction.Auto

值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

分段按钮组件的按钮未选中态的文本颜色。

值为undefined时，颜色为$r('sys.color.ohos_id_color_text_secondary')。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: DimensionNoPercentage
```

按钮未选中态的字体大小（不支持百分比设置）。

默认值：$r('sys.float.ohos_id_text_size_body2')

值为undefined时，按默认值处理。

**类型：** DimensionNoPercentage

**默认值：** $r('sys.float.ohos_id_text_size_body2')

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

按钮未选中态的字体粗细。

默认值：FontWeight.Regular

值为undefined时，按默认值处理。

**类型：** FontWeight

**默认值：** FontWeight.Regular

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: SizeOptions
```

图片尺寸。

默认值：{ width: 24, height: 24 }

单位：vp

值为undefined时，按默认值处理。

**说明：**

`imageSize`属性仅对图标按钮和图标+文本按钮生效，对纯文本按钮无效果。

**类型：** SizeOptions

**默认值：** SizeOptions { width: 24, height: 24 }

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
itemBorderRadius?: LengthMetrics
```

分段按钮中按钮项的边框圆角半径。

**说明：**

此属性仅在borderRadiusMode为BorderRadiusMode.CUSTOM时生效。

对于胶囊类多选按钮(type为"capsule"且multiply为true)，只能控制两端的选项圆角。

圆角大小受组件尺寸限制，最大值为组件宽或高的一半，不支持百分比设置。

默认值：`$r('sys.float.segmentbutton_selected_background_shape')`

值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedButtonPadding

```TypeScript
localizedButtonPadding?: LocalizedPadding
```

按钮内边距。

默认值：

仅图标按钮和仅文字按钮默认值：
`{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }`

图标+文本按钮默认值：
`{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8) }`

值为undefined时，按默认值处理。

**类型：** LocalizedPadding

**默认值：** For text only / icon only buttons LocalizedPadding
{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }
.
For text & icon buttons LocalizedPadding
{{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8)
}.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedTextPadding

```TypeScript
localizedTextPadding?: LocalizedPadding
```

文本内边距。

默认值：0

值为undefined时，按默认值处理。

**类型：** LocalizedPadding

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ResourceColor
```

分段按钮组件的按钮选中态背景板颜色。

值为undefined时，type为"tab"时，背景板颜色为`$r('sys.color.segment_button_checked_foreground_color')`。

type为"capsule"时，背景板颜色为`$r('sys.color.ohos_id_color_emphasize')`。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor?: ResourceColor
```

分段按钮组件的按钮选中态的文本颜色。

值为undefined时，type为"tab"时，颜色为`$r('sys.color.ohos_id_color_text_primary')`。

type为"capsule"时，颜色为`$r('sys.color.ohos_id_color_foreground_contrary')`。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontSize

```TypeScript
selectedFontSize?: DimensionNoPercentage
```

按钮选中态的字体大小（不支持百分比设置）。

默认值：$r('sys.float.ohos_id_text_size_body2')

值为undefined时，按默认值处理。

**类型：** DimensionNoPercentage

**默认值：** $r('sys.float.ohos_id_text_size_body2')

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedFontWeight

```TypeScript
selectedFontWeight?: FontWeight
```

按钮选中态的字体粗细。

默认值：FontWeight.Medium

值为undefined时，按默认值处理。

**类型：** FontWeight

**默认值：** FontWeight.Medium

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textPadding

```TypeScript
textPadding?: Padding | Dimension
```

文本内边距。

默认值：0

单位：vp

值为undefined时，按默认值处理。

**类型：** Padding | Dimension

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

