# OperateItem

列表右侧显示的元素类型。 同时配置多个属性时，按button、symbolStyle、image、icon与text组合、arrow、text、radio、checkbox、switch、icon的优先级选择右侧显示内容。icon可与text或subIcon组 合，arrow可与text组合；其他情况下仅显示优先级最高的内容。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-export declare class OperateItem--><!--Device-unnamed-export declare class OperateItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrow

```TypeScript
arrow?: OperateIcon
```

右侧元素为箭头，大小为12*24vp。 默认不设置或设置为undefined，右侧箭头不显示。

**类型：** [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-arrow?: OperateIcon--><!--Device-OperateItem-arrow?: OperateIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
button?: OperateButton
```

右侧元素为按钮。 默认不设置或设置为undefined，右侧按钮不显示。

**类型：** [OperateButton](arkts-arkui-arkui-advanced-composelistitem-operatebutton-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-button?: OperateButton--><!--Device-OperateItem-button?: OperateButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkbox

```TypeScript
checkbox?: OperateCheck
```

右侧元素为多选框，大小为24*24vp。 默认不设置或设置为undefined，右侧多选框不显示。

**类型：** [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-checkbox?: OperateCheck--><!--Device-OperateItem-checkbox?: OperateCheck-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: OperateIcon
```

右侧元素的第一个图标，大小为24*24vp。 默认不设置或设置为undefined，右侧图标不显示。

**类型：** [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-icon?: OperateIcon--><!--Device-OperateItem-icon?: OperateIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image?: ResourceStr
```

右侧元素为图片，大小为48*48vp。 默认不设置或设置为undefined，右侧图片不显示。

**类型：** ResourceStr

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-image?: ResourceStr--><!--Device-OperateItem-image?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radio

```TypeScript
radio?: OperateCheck
```

右侧元素为单选框，大小为24*24vp。 默认不设置或设置为undefined，右侧单选框不显示。

**类型：** [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-radio?: OperateCheck--><!--Device-OperateItem-radio?: OperateCheck-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subIcon

```TypeScript
subIcon?: OperateIcon
```

右侧元素的第二个图标，大小为24*24vp。 默认不设置或设置为undefined，右侧第二个图标不显示。

**类型：** [OperateIcon](arkts-arkui-arkui-advanced-composelistitem-operateicon-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-subIcon?: OperateIcon--><!--Device-OperateItem-subIcon?: OperateIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## switch

```TypeScript
switch?: OperateCheck
```

右侧元素为开关。 默认不设置或设置为undefined，右侧开关不显示。

**类型：** [OperateCheck](arkts-arkui-arkui-advanced-composelistitem-operatecheck-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-switch?: OperateCheck--><!--Device-OperateItem-switch?: OperateCheck-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

右侧元素为Symbol图标资源，大小为48*48vp，优先级大于image，同时设置时只显示Symbol图标。 默认不设置或设置为undefined，右侧Symbol图标不显示。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-symbolStyle?: SymbolGlyphModifier--><!--Device-OperateItem-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: ResourceStr
```

右侧元素为文字。 默认不设置或设置为undefined，右侧文字不显示。

**类型：** ResourceStr

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItem-text?: ResourceStr--><!--Device-OperateItem-text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

