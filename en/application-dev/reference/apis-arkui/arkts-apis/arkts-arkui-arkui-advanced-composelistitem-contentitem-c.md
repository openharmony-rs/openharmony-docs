# ContentItem

Defines elements for the left and center areas of the **ComposeListItem** component.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItem, ContentItem, IconType, OperateButton, OperateCheck, OperateIcon, OperateItem } from '@kit.ArkUI';
```

## description

```TypeScript
description?: ResourceStr
```

Description of the element in the center.

If this parameter is not set or is set to **undefined**, the description is not displayed.

**Text processing rules**: Text will wrap to a new line when it exceeds the length limit.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon resource of the element on the left.

If this parameter is not set or is set to **undefined**, the icon is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
iconStyle?: IconType
```

Icon style of the element on the left.

If this parameter is not set or is set to **undefined**, the icon is not displayed.

**Type:** [IconType](arkts-arkui-arkui-advanced-composelistitem-icontype-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryText

```TypeScript
primaryText?: ResourceStr
```

Primary text of the element in the center.

If this parameter is not set or is set to **undefined**, the primary text is not displayed.

**Text processing rules**: Text will wrap to a new line when it exceeds the length limit.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryText

```TypeScript
secondaryText?: ResourceStr
```

Secondary text of the element in the center.

If this parameter is not set or is set to **undefined**, the secondary text is not displayed.

**Text processing rules**: Text will wrap to a new line when it exceeds the length limit.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource of the element on the left, which has higher priority than **icon**. If both **icon** and this parameter are set, only the symbol icon is displayed.

If this parameter is not set or is set to **undefined**, the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
