# PromptOptionsV2

```TypeScript
export declare class PromptOptionsV2
```

Defines the configuration information of the exception prompt component.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class PromptOptionsV2--><!--Device-unnamed-export declare class PromptOptionsV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config?: PromptOptionsV2Config)
```

Constructor of **PromptOptionsV2**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)--><!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [PromptOptionsV2Config](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2config-i.md) | No | Configuration information of **PromptOptionsV2**. If **config** is not passed, the default values are used: **marginType** is **MarginTypeV2.DEFAULT_MARGIN** and **marginTop** is **0**. |

## actionText

```TypeScript
actionText?: ResourceStr
```

Text content of the right icon button of the current exception prompt.

Not set by default or set to **undefined**, the text content is not displayed.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-actionText?: ResourceStr--><!--Device-PromptOptionsV2-actionText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Exception icon style of the current exception prompt.

Not set by default or set to **undefined**, the exception icon is not displayed.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-icon?: ResourceStr--><!--Device-PromptOptionsV2-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

Whether to show the current exception prompt.

**true**: shown.

**false**: hidden.

Default value: **false**

**Decorator:** @Trace

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-isShown?: boolean--><!--Device-PromptOptionsV2-isShown?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop: Dimension
```

Top margin of the current exception prompt.

**Decorator:** @Trace

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-marginTop: Dimension--><!--Device-PromptOptionsV2-marginTop: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
marginType: MarginTypeV2
```

Margin type of the current exception prompt.

**Decorator:** @Trace

**Type:** [MarginTypeV2](arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-marginType: MarginTypeV2--><!--Device-PromptOptionsV2-marginType: MarginTypeV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Exception symbol icon style of the current exception prompt, with higher priority than **icon**.

Not set by default or set to **undefined**, the symbol icon is not displayed.

**Decorator:** @Trace

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
tip?: ResourceStr
```

Text prompt content of the current exception prompt.

Supports custom resources or the following four system resource strings for statuses.

1. No network status: displays network not connected, referencing **$r('sys.string.ohos_network_not_connected')**.
2. Poor network status: displays network connection unstable, tap to retry, referencing **$r('sys.string.ohos_network_connected_unstable')**.
3. Unable to connect to server status: displays unable to connect to server, tap to retry, **referencing $r('sys.string.ohos_unstable_connect_server')**.
4. Network available but unable to obtain location status: displays unable to obtain location, tap to retry, referencing **$r('sys.string.ohos_custom_network_tips_left')**.

Not set by default or set to **undefined**, the text prompt content is not displayed.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2-tip?: ResourceStr--><!--Device-PromptOptionsV2-tip?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
