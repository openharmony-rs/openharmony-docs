# ButtonLabelStyle

按钮中文本的显示样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ButtonLabelStyle--><!--Device-unnamed-export declare interface ButtonLabelStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

设置label文本字体样式。 默认值：默认值参考[Font]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** Font

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-font?: Font--><!--Device-ButtonLabelStyle-font?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy?: TextHeightAdaptivePolicy
```

设置label文本自适应高度的方式。 默认值：TextHeightAdaptivePolicy.MAX\_LINES\_FIRST

**类型：** TextHeightAdaptivePolicy

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy--><!--Device-ButtonLabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: double | ResourceStr
```

设置label文本最大显示字号。需配合minFontSize以及maxLines或布局大小限制使用。

**类型：** double \| ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-maxFontSize?: double | ResourceStr--><!--Device-ButtonLabelStyle-maxFontSize?: double | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: int
```

设置label文本的最大行数。如果指定此参数，则文本最多不会超过指定的行。如果有多余的文本，可以通过overflow来指定截断方式。 默认值：1

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-maxLines?: int--><!--Device-ButtonLabelStyle-maxLines?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: double | ResourceStr
```

设置label文本最小显示字号。需配合maxFontSize以及maxLines或布局大小限制使用。 **说明：** minFontSize小于或等于0时，自适应字号不生效。

**类型：** double \| ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-minFontSize?: double | ResourceStr--><!--Device-ButtonLabelStyle-minFontSize?: double | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

设置label文本超长时的显示方式。文本截断是按字截断。例如，英文以单词为最小单位进行截断，若需要以字母为单位进行截断，可在字母间添加零宽空格。 默认值：TextOverflow.Ellipsis

**类型：** TextOverflow

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-overflow?: TextOverflow--><!--Device-ButtonLabelStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

设置内容的水平对齐模式。 默认值：TextAlign.Start **设备差异：** 默认值是TextAlign.Start。在穿戴设备上，默认值为TextAlign.Center。

**类型：** TextAlign

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonLabelStyle-textAlign?: TextAlign--><!--Device-ButtonLabelStyle-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

