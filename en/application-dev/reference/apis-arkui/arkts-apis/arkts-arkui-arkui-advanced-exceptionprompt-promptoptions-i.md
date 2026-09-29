# PromptOptions

```TypeScript
export interface PromptOptions
```

Defines the exception prompt options.

**Since:** 11

<!--Device-unnamed-export interface PromptOptions--><!--Device-unnamed-export interface PromptOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MarginType, PromptOptions, ExceptionPrompt } from '@kit.ArkUI';
```

## actionText

```TypeScript
actionText?: ResourceStr
```

Text of the icon on the right of the exception prompt.

If this parameter is not set or is set to **undefined**, the text is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PromptOptions-actionText?: ResourceStr--><!--Device-PromptOptions-actionText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon style of the exception prompt.

If this parameter is not set or is set to **undefined**, the icon is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PromptOptions-icon?: ResourceStr--><!--Device-PromptOptions-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

Whether the exception prompt is displayed.

**true**: The exception prompt is displayed.

**false**: The exception prompt is hidden.

Default value: **false**.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PromptOptions-isShown?: boolean--><!--Device-PromptOptions-isShown?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop: Dimension
```

Top margin of the exception prompt.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PromptOptions-marginTop: Dimension--><!--Device-PromptOptions-marginTop: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
marginType: MarginType
```

Margin type of the exception prompt.

**Type:** [MarginType](arkts-arkui-arkui-advanced-exceptionprompt-margintype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PromptOptions-marginType: MarginType--><!--Device-PromptOptions-marginType: MarginType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon style of the exception prompt, which has higher priority than **icon**.

If this parameter is not set or is set to **undefined**, the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PromptOptions-symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptions-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
tip?: ResourceStr
```

Text content of the exception prompt.

By default, the following text resources are provided:

1. **ohos_network_not_connected**: displayed when there is no Internet connection.
2. **ohos_network_connected_unstable**: displayed when the Internet connection is unstable.
3. **ohos_unstable_connect_server**: displayed when the server fails to be connected.
4. **ohos_custom_network_tips_left**: displayed when an Internet connection is available but the location fails to be obtained.

If this parameter is not set or is set to **undefined**, the text content is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PromptOptions-tip?: ResourceStr--><!--Device-PromptOptions-tip?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
