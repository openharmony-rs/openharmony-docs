# TextPickerTextStyle

文本样式选项，继承自PickerTextStyle。

**继承/实现关系：** TextPickerTextStyle extends PickerTextStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface TextPickerTextStyle--><!--Device-unnamed-export declare interface TextPickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: double | string | Resource
```

文本最大显示字号。详细规则请参考Text组件的maxFontSize属性。

**类型：** double \| string \| [Resource](../../apis-arkui/arkts-apis/arkts-arkui-resource-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerTextStyle-maxFontSize?: double | string | Resource--><!--Device-TextPickerTextStyle-maxFontSize?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: double | string | Resource
```

文本最小显示字号，与maxFontSize配合使用。当设置minFontSize和maxFontSize时，font中的size将不生效。默认最大行数为1， 自适应高度方式为MIN_FONT_SIZE_FIRST。详细规则请参考Text组件的minFontSize属性。

**类型：** double \| string \| [Resource](../../apis-arkui/arkts-apis/arkts-arkui-resource-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerTextStyle-minFontSize?: double | string | Resource--><!--Device-TextPickerTextStyle-minFontSize?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

文本截断方式。当设置为MARQUEE时，该属性不生效。 详细规则请参考Text组件的textOverflow属性。

**类型：** [TextOverflow](../../apis-arkui/arkts-apis/arkts-arkui-textoverflow-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextPickerTextStyle-overflow?: TextOverflow--><!--Device-TextPickerTextStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

