# TextPickerTextStyle

文本样式选项，继承自[PickerTextStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** TextPickerTextStyle extends [PickerTextStyle](../../../apis-na/arkts-apis/arkts-na-component/common-pickertextstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextPickerTextStyle extends PickerTextStyle--><!--Device-unnamed-export declare interface TextPickerTextStyle extends PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: double | string | Resource
```

文本最大显示字号。详细规则请参考Text组件的[maxFontSize]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性。

**类型：** double \| string \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerTextStyle-maxFontSize?: double | string | Resource--><!--Device-TextPickerTextStyle-maxFontSize?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: double | string | Resource
```

文本最小显示字号，与maxFontSize配合使用。当设置minFontSize和maxFontSize时，font中的size将不生效。默认最大行数为1， 自适应高度方式为MIN\_FONT\_SIZE\_FIRST。详细规则请参考Text组件的[minFontSize]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性。

**类型：** double \| string \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerTextStyle-minFontSize?: double | string | Resource--><!--Device-TextPickerTextStyle-minFontSize?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

文本截断方式。当设置为MARQUEE时，该属性不生效。 详细规则请参考Text组件的[textOverflow]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_属性。

**类型：** TextOverflow

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerTextStyle-overflow?: TextOverflow--><!--Device-TextPickerTextStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

