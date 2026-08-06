# LabelStyle

label文本和字体的样式对象。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare interface LabelStyle--><!--Device-unnamed-declare interface LabelStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

设置label文本字体样式。 当页签为子页签时，默认值是字体大小16.0fp、字体类型'HarmonyOS Sans'，字体风格正常，选中时字重中等，未选中时字重正常。 当页签为底部页签时，默认值是字体大小10.0fp、字体类型'HarmonyOS Sans'，字体风格正常，字重中等。 从API version 12开始，底部页签内容左右排布时默认字体大小为12.0fp。

**类型：** Font

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-font?: Font--><!--Device-LabelStyle-font?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy?: TextHeightAdaptivePolicy
```

设置Label文本自适应高度的方式。默认值是最大行数优先。

**类型：** TextHeightAdaptivePolicy

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy--><!--Device-LabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

设置label文本最大显示字号（不支持百分比设置）。需配合minFontSize以及maxLines或布局大小限制使用。自适应文本大小生效后，font.size不生效。默认值是0.0fp，即默认自适应文本大小不生效。 取值范围：[minFontSize, +∞)。异常值时取默认值。

**类型：** number \| ResourceStr

**默认值：** 0.0fp [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-maxFontSize?: number | ResourceStr--><!--Device-LabelStyle-maxFontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

设置label文本的最大行数。如果指定此参数，则文本最多不会超过指定的行。如果有多余的文本，可以通过textOverflow来指定截断方式。默认值是1。 取值范围：[1, +∞)。异常值时取默认值。

**类型：** number

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-maxLines?: number--><!--Device-LabelStyle-maxLines?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

设置label文本最小显示字号（不支持百分比设置）。需配合maxFontSize以及maxLines或布局大小限制使用。自适应文本大小生效后，font.size不生效。默认值是0.0fp，即默认自适应文本大小不生效。 取值范围：(0, +∞)。异常值时取默认值。

**类型：** number \| ResourceStr

**默认值：** 0.0fp [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-minFontSize?: number | ResourceStr--><!--Device-LabelStyle-minFontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

设置label文本超长时的显示方式。默认值是省略号截断。

**类型：** TextOverflow

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-overflow?: TextOverflow--><!--Device-LabelStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedColor

```TypeScript
selectedColor?: ResourceColor
```

设置label文本字体选中时的颜色。 默认值：#FF007DFF

**类型：** ResourceColor

**默认值：** #FF007DFF

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-selectedColor?: ResourceColor--><!--Device-LabelStyle-selectedColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unselectedColor

```TypeScript
unselectedColor?: ResourceColor
```

设置label文本字体未选中时的颜色。 默认值：#99182431

**类型：** ResourceColor

**默认值：** #99182431

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-unselectedColor?: ResourceColor--><!--Device-LabelStyle-unselectedColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

