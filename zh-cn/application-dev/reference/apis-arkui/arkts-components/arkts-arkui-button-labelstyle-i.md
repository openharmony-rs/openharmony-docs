# LabelStyle

Button组件的label文本及其字体样式。

**起始版本：** 10

<!--Device-unnamed-declare interface LabelStyle--><!--Device-unnamed-declare interface LabelStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

设置label文本字体样式。

默认值：

{

size:'16.0fp',

weight:FontWeight.Medium,

style:FontStyle.Normal,

family:'HarmonyOS Sans'

}

**类型：** Font

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-font?: Font--><!--Device-LabelStyle-font?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy?: TextHeightAdaptivePolicy
```

设置label文本自适应高度的方式。

默认值：TextHeightAdaptivePolicy.MAX_LINES_FIRST

**类型：** TextHeightAdaptivePolicy

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy--><!--Device-LabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

设置label文本最大显示字号。需配合minFontSize以及maxLines或布局大小限制使用。为number类型时默认单位：fp。

**类型：** number | ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-maxFontSize?: number | ResourceStr--><!--Device-LabelStyle-maxFontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

设置label文本的最大行数。如果指定此参数，则文本最多不会超过指定的行。如果有多余的文本，可以通过overflow来指定截断方式。

默认值：1

**说明：**

设置小于等于0的值时，按默认值处理。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-maxLines?: number--><!--Device-LabelStyle-maxLines?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

设置label文本最小显示字号。需配合maxFontSize以及maxLines或布局大小限制使用。

**说明：**

minFontSize小于或等于0时，自适应字号不生效。为number类型时默认单位：fp。

**类型：** number | ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-minFontSize?: number | ResourceStr--><!--Device-LabelStyle-minFontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

设置label文本超长时的显示方式。文本截断是按字截断。例如，英文以单词为最小单位进行截断，若需要以字母为单位进行截断，可在字母间添加零宽空格。

默认值：TextOverflow.Ellipsis

**类型：** TextOverflow

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-overflow?: TextOverflow--><!--Device-LabelStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

设置label文本在水平方向上的对齐方式，label文本被截断时生效。当使用子节点的Text组件设置label时，此属性不生效，实际的文本对齐方式由子节点Text组件的textAlign属性决定。

Wearable设备默认值为TextAlign.Center，其他设备默认值为TextAlign.Start。

**类型：** TextAlign

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LabelStyle-textAlign?: TextAlign--><!--Device-LabelStyle-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

