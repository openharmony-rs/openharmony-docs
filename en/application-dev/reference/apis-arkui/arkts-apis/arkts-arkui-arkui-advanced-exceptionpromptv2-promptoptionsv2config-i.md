# PromptOptionsV2Config

```TypeScript
export interface PromptOptionsV2Config
```

Defines the configuration information API for constructing a **PromptOptionsV2** object.

**Since:** 26.0.0

<!--Device-unnamed-export interface PromptOptionsV2Config--><!--Device-unnamed-export interface PromptOptionsV2Config-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## actionText

```TypeScript
actionText?: ResourceStr
```

Text content of the right icon button of the current exception prompt.

Not set by default or set to **undefined**, the text content is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-actionText?: ResourceStr--><!--Device-PromptOptionsV2Config-actionText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Exception icon style of the current exception prompt.

Not set by default or set to **undefined**, the exception icon is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-icon?: ResourceStr--><!--Device-PromptOptionsV2Config-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

Visibility state of the current exception prompt.

**true**: shown.

**false**: hidden.

Default value: **false**

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-isShown?: boolean--><!--Device-PromptOptionsV2Config-isShown?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop: Dimension
```

Top margin of the current exception prompt.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-marginTop: Dimension--><!--Device-PromptOptionsV2Config-marginTop: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
marginType: MarginTypeV2
```

Margin type of the current exception prompt.

**Type:** [MarginTypeV2](arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-marginType: MarginTypeV2--><!--Device-PromptOptionsV2Config-marginType: MarginTypeV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Exception symbol icon style of the current exception prompt, which takes priority over **icon**.

Not set by default or set to **undefined**, the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2Config-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
tip?: ResourceStr
```

Text content of the current exception prompt.

Supports custom resources or the following four system resource strings for status text.

1. No network state: Show network not connected, referencing **$r('sys.string.ohos_network_not_connected')**.
2. Poor network state: Show network connection is unstable, tap to retry, referencing **$r('sys.string.ohos_network_connected_unstable')**.
3. Unable to connect to server state: Show unable to connect to server, tap to retry, referencing **$r('sys.string.ohos_unstable_connect_server')**.
4. Network available but unable to obtain location state: Show unable to obtain location, tap to retry, referencing **$r('sys.string.ohos_custom_network_tips_left')**.

Not set by default or set to **undefined**, the text content is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-PromptOptionsV2Config-tip?: ResourceStr--><!--Device-PromptOptionsV2Config-tip?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
