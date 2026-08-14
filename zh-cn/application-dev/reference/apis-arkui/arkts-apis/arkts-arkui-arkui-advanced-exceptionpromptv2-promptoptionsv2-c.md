# PromptOptionsV2

PromptOptionsV2用于定义异常提示组件的配置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class PromptOptionsV2--><!--Device-unnamed-export declare class PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config?: PromptOptionsV2Config)
```

PromptOptionsV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)--><!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [PromptOptionsV2Config](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2config-i.md) | 否 | PromptOptionsV2的配置信息。如果不传入config，则使用默认值：marginType为MarginTypeV2 .DEFAULT_MARGIN，marginTop为0。 |

## actionText

```TypeScript
@Trace
  actionText?: ResourceStr
```

指定当前异常提示的右侧图标按钮的文字内容。 默认不设置或设置为undefined，文字内容不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  actionText?: ResourceStr--><!--Device-PromptOptionsV2-@Trace  actionText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
@Trace
  icon?: ResourceStr
```

指定当前异常提示的异常图标样式。 默认不设置或设置为undefined，不显示异常图标。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  icon?: ResourceStr--><!--Device-PromptOptionsV2-@Trace  icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
@Trace
  isShown?: boolean
```

指定当前异常提示的显隐状态。 true：显示状态。 false：隐藏状态。 默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  isShown?: boolean--><!--Device-PromptOptionsV2-@Trace  isShown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
@Trace
  marginTop: Dimension
```

指定当前异常提示的距离顶部的位置。

**类型：** Dimension

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  marginTop: Dimension--><!--Device-PromptOptionsV2-@Trace  marginTop: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
@Trace
  marginType: MarginTypeV2
```

指定当前异常提示的边距样式。

**类型：** [MarginTypeV2](arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  marginType: MarginTypeV2--><!--Device-PromptOptionsV2-@Trace  marginType: MarginTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
@Trace
  symbolStyle?: SymbolGlyphModifier
```

指定当前异常提示的异常Symbol图标样式，优先级大于icon。 默认不设置或设置为undefined，Symbol图标不显示。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2-@Trace  symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
@Trace
  tip?: ResourceStr
```

指定当前异常提示的文字提示内容。 支持自定义资源，或如下四种状态文字系统资源。 1. 无网络状态：显示网络未连接，引用\$r('sys.string.ohos_network_not_connected')。 2. 网络差状态：显示网络连接不稳定，请点击重试，引用\$r('sys.string.ohos_network_connected_unstable')。 3. 连不上服务器状态：显示无法连接到服务器，请点击重试，引用\$r('sys.string.ohos_unstable_connect_server')。 4. 有网但是获取不到位置状态：显示无法获取位置，请点击重试，引用\$r('sys.string.ohos_custom_network_tips_left')。 默认不设置或设置为undefined，文字提示内容不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-@Trace  tip?: ResourceStr--><!--Device-PromptOptionsV2-@Trace  tip?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

