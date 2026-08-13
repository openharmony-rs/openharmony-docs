# TextStyle

文本字体样式对象说明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class TextStyle--><!--Device-unnamed-export declare class TextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value?: TextStyleInterface)
```

文本字体样式的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-constructor(value?: TextStyleInterface)--><!--Device-TextStyle-constructor(value?: TextStyleInterface)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextStyleInterface](arkts-arkui-styledstring-textstyleinterface-i.md) | 否 | 字体样式设置项。 |

## fontColor

```TypeScript
readonly fontColor?: ResourceColor
```

获取属性字符串的文本颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontColor?: ResourceColor--><!--Device-TextStyle-readonly fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontConfigs

```TypeScript
readonly fontConfigs?: FontConfigs
```

获取属性字符串的字体配置。 默认返回undefined，表示未设置fontConfigs。

**类型：** [FontConfigs](arkts-arkui-textcommon-fontconfigs-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontConfigs?: FontConfigs--><!--Device-TextStyle-readonly fontConfigs?: FontConfigs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
readonly fontFamily?: string
```

获取属性字符串的文本字体。 默认返回undefined。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontFamily?: string--><!--Device-TextStyle-readonly fontFamily?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
readonly fontSize?: double
```

获取属性字符串的文本字体大小。 单位：[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontSize?: double--><!--Device-TextStyle-readonly fontSize?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
readonly fontStyle?: FontStyle
```

获取属性字符串的文本字体样式。

**类型：** [FontStyle](arkts-arkui-fontstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontStyle?: FontStyle--><!--Device-TextStyle-readonly fontStyle?: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontVariations

```TypeScript
readonly fontVariations?: Array<FontVariation>
```

获取可变字体的属性数组。 默认值：undefined，表示未设置可变字体的属性。

**类型：** Array&lt;[FontVariation](arkts-arkui-fontvariation-t.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontVariations?: Array<FontVariation>--><!--Device-TextStyle-readonly fontVariations?: Array<FontVariation>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
readonly fontWeight?: int
```

获取属性字符串的文本字体粗细。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly fontWeight?: int--><!--Device-TextStyle-readonly fontWeight?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
readonly strokeColor?: ResourceColor
```

获取属性字符串的文本描边颜色。 默认返回字体颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly strokeColor?: ResourceColor--><!--Device-TextStyle-readonly strokeColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
readonly strokeJoinStyle?: StrokeJoinStyle
```

获取属性字符串的文本描边拐角样式。 默认值：StrokeJoinStyle.MITER_JOIN。

**类型：** [StrokeJoinStyle](arkts-arkui-textcommon-strokejoinstyle-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly strokeJoinStyle?: StrokeJoinStyle--><!--Device-TextStyle-readonly strokeJoinStyle?: StrokeJoinStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
readonly strokeWidth?: double
```

获取属性字符串的文本描边宽度。 默认返回0，单位为[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly strokeWidth?: double--><!--Device-TextStyle-readonly strokeWidth?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## superscript

```TypeScript
readonly superscript?: SuperscriptStyle
```

获取属性字符串的文本上下角标。 默认值：SuperscriptStyle.NORMAL。

**类型：** [SuperscriptStyle](arkts-arkui-textcommon-superscriptstyle-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextStyle-readonly superscript?: SuperscriptStyle--><!--Device-TextStyle-readonly superscript?: SuperscriptStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

