# PromptOptionsV2

Configuration parameter of ExceptionPromptV2. Use @ObservedV2 and @Trace to support deep observation and dynamic refresh of properties.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class PromptOptionsV2--><!--Device-unnamed-export declare class PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config?: PromptOptionsV2Config)
```

Constructor of PromptOptionsV2.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)--><!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [PromptOptionsV2Config](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2config-i.md) | 否 | Configuration information of ExceptionPromptV2 |

## actionText

```TypeScript
@Trace
  public actionText?: ResourceStr
```

Text of the icon on the right of the ExceptionPromptV2. If this parameter is not set or is set to undefined, the text is not displayed.

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public actionText?: ResourceStr--><!--Device-PromptOptionsV2-@Trace  public actionText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
@Trace
  public icon?: ResourceStr
```

Icon style of the ExceptionPromptV2. If this parameter is not set or is set to undefined, the icon is not displayed.

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public icon?: ResourceStr--><!--Device-PromptOptionsV2-@Trace  public icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
@Trace
  public isShown?: boolean
```

Whether the ExceptionPromptV2 is displayed. true: The exception prompt is displayed. false: The exception prompt is hidden. Default value: false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public isShown?: boolean--><!--Device-PromptOptionsV2-@Trace  public isShown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
@Trace
  public marginTop: Dimension
```

Top margin of the ExceptionPromptV2. Distance from the top to the content area of ExceptionPromptV2.

**类型：** Dimension

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public marginTop: Dimension--><!--Device-PromptOptionsV2-@Trace  public marginTop: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
@Trace
  public marginType: MarginTypeV2
```

Margin Type of ExceptionPromptV2. Margin from the content area to the edge of the container.

**类型：** [MarginTypeV2](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public marginType: MarginTypeV2--><!--Device-PromptOptionsV2-@Trace  public marginType: MarginTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
@Trace
  public symbolStyle?: SymbolGlyphModifier
```

Symbol icon style of the ExceptionPromptV2, which has higher priority than icon. If this parameter is not set or is set to undefined, the symbol icon is not displayed.

**类型：** [SymbolGlyphModifier](../../apis-arkui/arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2-@Trace  public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
@Trace
  public tip?: ResourceStr
```

Text content of the ExceptionPromptV2. By default, the following text resources are provided: 1. ohos_network_not_connected: displayed when no Internet connection. 2. ohos_network_connected_unstable: displayed when the Internet connection is unstable. 3. ohos_unstable_connect_server: displayed when the server fails to be connected. 4. ohos_custom_network_tips_left: displayed when an Internet connection is available but the location fails to be obtained. If this parameter is not set or is set to undefined, the text content is not displayed.

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-@Trace  public tip?: ResourceStr--><!--Device-PromptOptionsV2-@Trace  public tip?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

