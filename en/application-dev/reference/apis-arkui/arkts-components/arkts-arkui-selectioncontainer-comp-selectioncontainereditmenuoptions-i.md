# SelectionContainerEditMenuOptions

```TypeScript
export interface SelectionContainerEditMenuOptions
```

Provides the custom edit menu options of **SelectionContainer**.

**Since:** 26.0.0

<!--Device-unnamed-export interface SelectionContainerEditMenuOptions--><!--Device-unnamed-export interface SelectionContainerEditMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## onCreateMenu

```TypeScript
onCreateMenu?: OnCreateMenuCallback
```

Triggered before the menu is displayed each time. It passes in the default menu items and returns the processed menu items. The default value is empty, and this callback is not triggered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerEditMenuOptions-onCreateMenu?: OnCreateMenuCallback--><!--Device-SelectionContainerEditMenuOptions-onCreateMenu?: OnCreateMenuCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMenuItemClick

```TypeScript
onMenuItemClick?: OnMenuItemClickWithTextCallback
```

Triggered when a menu item is clicked. It can intercept the default menu execution behavior of the system. The default value is empty, and this callback is not triggered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerEditMenuOptions-onMenuItemClick?: OnMenuItemClickWithTextCallback--><!--Device-SelectionContainerEditMenuOptions-onMenuItemClick?: OnMenuItemClickWithTextCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPrepareMenu

```TypeScript
onPrepareMenu?: OnPrepareMenuCallback
```

Triggered after the selected text content changes and before the menu is displayed. The menu data can be adjusted in this callback. The default value is empty, and this callback is not triggered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerEditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback--><!--Device-SelectionContainerEditMenuOptions-onPrepareMenu?: OnPrepareMenuCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
