# TextPickerTextStyle

文本样式选项，继承自[PickerTextStyle](arkts-arkui-common-pickertextstyle-i.md)。

**继承/实现关系：** TextPickerTextStyle extends [PickerTextStyle](arkts-arkui-common-pickertextstyle-i.md)

**起始版本：** 15

<!--Device-unnamed-declare interface TextPickerTextStyle extends PickerTextStyle--><!--Device-unnamed-declare interface TextPickerTextStyle extends PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | string | Resource
```

文本最大显示字号。详细规则请参考Text组件的[maxFontSize](TextAttribute#maxFontSize)属性。

**类型：** number | string | Resource

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerTextStyle-maxFontSize?: number | string | Resource--><!--Device-TextPickerTextStyle-maxFontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | string | Resource
```

文本最小显示字号，与maxFontSize配合使用。当设置minFontSize和maxFontSize时，font中的size将不生效。默认最大行数为1，自适应高度方式为MIN_FONT_SIZE_FIRST。详细规则请参考Text组件的[minFontSize](TextAttribute#minFontSize)属性。

**类型：** number | string | Resource

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerTextStyle-minFontSize?: number | string | Resource--><!--Device-TextPickerTextStyle-minFontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

文本截断方式。当设置为MARQUEE时，该属性不生效。详细规则请参考Text组件的[textOverflow](TextAttribute#textOverflow)属性。

**类型：** TextOverflow

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerTextStyle-overflow?: TextOverflow--><!--Device-TextPickerTextStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

