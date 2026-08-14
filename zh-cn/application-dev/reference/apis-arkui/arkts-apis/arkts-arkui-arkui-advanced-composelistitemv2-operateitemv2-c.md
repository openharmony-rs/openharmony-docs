# OperateItemV2

列表项右侧显示的元素类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class OperateItemV2--><!--Device-unnamed-export declare class OperateItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: OperateItemV2Options)
```

OperateItemV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-constructor(options?: OperateItemV2Options)--><!--Device-OperateItemV2-constructor(options?: OperateItemV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OperateItemV2Options](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | 否 | 列表项右侧属性配置。&lt;br/&gt;默认不设置或设置为undefined时，按各属性的默认效果创建对象。 |

## arrow

```TypeScript
@Trace
  public arrow?: OperateIconV2
```

列表项右侧元素为箭头，大小为12*24vp。 默认不设置或设置为undefined，列表项右侧箭头不显示。

**类型：** [OperateIconV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public arrow?: OperateIconV2--><!--Device-OperateItemV2-@Trace  public arrow?: OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
@Trace
  public button?: OperateButtonV2
```

列表项右侧元素为按钮。 默认不设置或设置为undefined，列表项右侧按钮不显示。

**类型：** [OperateButtonV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operatebuttonv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public button?: OperateButtonV2--><!--Device-OperateItemV2-@Trace  public button?: OperateButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkbox

```TypeScript
@Trace
  public checkbox?: OperateCheckV2
```

列表项右侧元素为多选框，大小为24*24vp。 默认不设置或设置为undefined，列表项右侧多选框不显示。

**类型：** [OperateCheckV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public checkbox?: OperateCheckV2--><!--Device-OperateItemV2-@Trace  public checkbox?: OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
@Trace
  public icon?: OperateIconV2
```

左侧元素的图标资源。 默认不设置或设置为undefined，表示不显示icon图标资源。 同时设置symbolStyle时，只显示Symbol图标。

**类型：** [OperateIconV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public icon?: OperateIconV2--><!--Device-OperateItemV2-@Trace  public icon?: OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
@Trace
  public image?: ResourceStr
```

列表项右侧元素为图片，大小为48*48vp。 默认不设置或设置为undefined，列表项右侧图片不显示。 同时设置symbolStyle时，只显示Symbol图标。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public image?: ResourceStr--><!--Device-OperateItemV2-@Trace  public image?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radio

```TypeScript
@Trace
  public radio?: OperateCheckV2
```

列表项右侧元素为单选框，大小为24*24vp。 默认不设置或设置为undefined，列表项右侧单选框不显示。

**类型：** [OperateCheckV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public radio?: OperateCheckV2--><!--Device-OperateItemV2-@Trace  public radio?: OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subIcon

```TypeScript
@Trace
  public subIcon?: OperateIconV2
```

列表项右侧元素的第二个图标，大小为24*24vp。 默认不设置或设置为undefined，列表项右侧第二个图标不显示。

**类型：** [OperateIconV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operateiconv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public subIcon?: OperateIconV2--><!--Device-OperateItemV2-@Trace  public subIcon?: OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
@Trace
  public symbolStyle?: SymbolGlyphModifier
```

列表项右侧元素为Symbol图标资源，大小为48*48vp，优先级大于image，同时设置时只显示Symbol图标。 默认不设置或设置为undefined，列表项右侧Symbol图标不显示。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public symbolStyle?: SymbolGlyphModifier--><!--Device-OperateItemV2-@Trace  public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
@Trace
  public text?: ResourceStr
```

列表项右侧元素为文字。 默认不设置或设置为undefined，列表项右侧文字不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public text?: ResourceStr--><!--Device-OperateItemV2-@Trace  public text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toggle

```TypeScript
@Trace
  public toggle?: OperateCheckV2
```

列表项右侧元素为开关。 默认不设置或设置为undefined，列表项右侧开关不显示。

**类型：** [OperateCheckV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operatecheckv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-@Trace  public toggle?: OperateCheckV2--><!--Device-OperateItemV2-@Trace  public toggle?: OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

