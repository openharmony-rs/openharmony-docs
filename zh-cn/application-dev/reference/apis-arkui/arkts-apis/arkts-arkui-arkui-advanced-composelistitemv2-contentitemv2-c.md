# ContentItemV2

列表左侧显示的图标、图标大小以及中间元素文字内容。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class ContentItemV2--><!--Device-unnamed-export declare class ContentItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: ContentItemV2Options)
```

ContentItemV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-constructor(options?: ContentItemV2Options)--><!--Device-ContentItemV2-constructor(options?: ContentItemV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContentItemV2Options](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-contentitemv2options-i.md) | 否 | 列表左侧属性配置。&lt;br/&gt;默认不设置或设置为undefined时，按各属性的默认效果创建对象。 |

## description

```TypeScript
@Trace
  public description?: ResourceStr
```

中间元素的描述内容。 默认不设置或设置为undefined时，不显示描述内容。 文本超长后无限换行显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-@Trace  public description?: ResourceStr--><!--Device-ContentItemV2-@Trace  public description?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
@Trace
  public icon?: ResourceStr
```

左侧元素的图标资源。 默认不设置或设置为undefined，表示不显示icon图标资源。 同时设置symbolStyle时，只显示Symbol图标。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-@Trace  public icon?: ResourceStr--><!--Device-ContentItemV2-@Trace  public icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
@Trace
  public iconStyle?: IconTypeV2
```

左侧元素的图标类型。 默认不设置或设置为undefined，表示不显示icon图标资源。

**类型：** [IconTypeV2](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-icontypev2-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-@Trace  public iconStyle?: IconTypeV2--><!--Device-ContentItemV2-@Trace  public iconStyle?: IconTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
@Trace
  public primaryText?: ResourceStr
```

中间元素的标题内容。 默认不设置或设置为undefined时，不显示标题内容。 文本超长后无限换行显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-@Trace  public primaryText?: ResourceStr--><!--Device-ContentItemV2-@Trace  public primaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
@Trace
  public secondaryText?: ResourceStr
```

中间元素的副标题内容。 默认不设置或设置为undefined时，不显示副标题内容。 文本超长后无限换行显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-@Trace  public secondaryText?: ResourceStr--><!--Device-ContentItemV2-@Trace  public secondaryText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
@Trace
  public symbolStyle?: SymbolGlyphModifier
```

左侧元素的Symbol图标资源，优先级大于icon，同时设置了icon和Symbol图标，只显示Symbol图标。 默认不设置或设置为undefined，Symbol图标不显示。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContentItemV2-@Trace  public symbolStyle?: SymbolGlyphModifier--><!--Device-ContentItemV2-@Trace  public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

