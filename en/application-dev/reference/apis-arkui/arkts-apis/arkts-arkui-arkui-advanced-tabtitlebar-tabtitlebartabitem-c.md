# TabTitleBarTabItem

```TypeScript
export declare class TabTitleBarTabItem
```

Declaration of the tab item.

**Since:** 10

<!--Device-unnamed-export declare class TabTitleBarTabItem--><!--Device-unnamed-export declare class TabTitleBarTabItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { TabTitleBar, TabTitleBarMenuItem, TabTitleBarTabItem } from '@kit.ArkUI';
```

## icon

```TypeScript
icon?: ResourceStr
```

Tab icon resource. If **symbolStyle** is set, this attribute does not take effect. If not set, the tab displays only text content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBarTabItem-icon?: ResourceStr--><!--Device-TabTitleBarTabItem-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource, which takes priority over **icon**. Pass this parameter when a symbol icon is needed as the tab. If not passed, the image tab set by the **icon** parameter is used.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabTitleBarTabItem-symbolStyle?: SymbolGlyphModifier--><!--Device-TabTitleBarTabItem-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Text content displayed on the tab item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBarTabItem-title: ResourceStr--><!--Device-TabTitleBarTabItem-title: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
