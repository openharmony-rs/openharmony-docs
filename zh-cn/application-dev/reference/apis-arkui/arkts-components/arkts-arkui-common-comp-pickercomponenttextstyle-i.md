# PickerComponentTextStyle

```TypeScript
declare interface PickerComponentTextStyle
```

定义DatePickerComponent与UIPickerComponent共用的文本样式。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface PickerComponentTextStyle--><!--Device-unnamed-declare interface PickerComponentTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

字体颜色。

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerComponentTextStyle-color?: ResourceColor--><!--Device-PickerComponentTextStyle-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

文本样式。仅支持size与weight。

**类型：** Font

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerComponentTextStyle-font?: Font--><!--Device-PickerComponentTextStyle-font?: Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

文本最大字号，与minFontSize配合使用以启用字号缩放。当minFontSize与maxFontSize同时设置时，font中的size不生效。详见TextAttribute的maxFontSize。

**类型：** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerComponentTextStyle-maxFontSize?: number | ResourceStr--><!--Device-PickerComponentTextStyle-maxFontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

文本最小字号，与maxFontSize配合使用以启用字号缩放。当minFontSize与maxFontSize同时设置时，font中的size不生效。详见TextAttribute的minFontSize。

**类型：** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerComponentTextStyle-minFontSize?: number | ResourceStr--><!--Device-PickerComponentTextStyle-minFontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

设置文本超长时的显示方式。设置为MARQUEE时不生效。详见TextAttribute的textOverflow。

**类型：** [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-PickerComponentTextStyle-overflow?: TextOverflow--><!--Device-PickerComponentTextStyle-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
