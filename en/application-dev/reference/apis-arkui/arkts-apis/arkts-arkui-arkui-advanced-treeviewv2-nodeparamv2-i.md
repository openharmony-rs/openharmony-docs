# NodeParamV2

```TypeScript
export interface NodeParamV2
```

Defines the node parameter API, which is used to configure the properties of a tree node.

**Since:** 26.0.0

<!--Device-unnamed-export interface NodeParamV2--><!--Device-unnamed-export interface NodeParamV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## container

```TypeScript
container?: OnContainerCallback
```

Right-click child component container bound to the node. The child component is decorated by **@Builder**. Pass this parameter when a right-click menu or custom right-click operation needs to be provided for the node. If it is not passed, the node does not display a right-click menu.

Default value: **() =&gt; void**, which means no right-click child component container is bound.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-container?: OnContainerCallback--><!--Device-NodeParamV2-container?: OnContainerCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId?: number
```

Current child node ID.

Value range: greater than or equal to -1.

It cannot be the root node ID or null; otherwise, an exception is thrown. Two identical **currentNodeId** values cannot be set.

Default value: **-1**, which means the node ID is not specified and is automatically assigned by the system.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-currentNodeId?: number--><!--Device-NodeParamV2-currentNodeId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## editIcon

```TypeScript
editIcon?: ResourceStr
```

Edit icon used to customize the icon displayed when the node enters the editing state. Pass this parameter when an icon different from the default state needs to be displayed in the node editing state. If it is not passed, the node displays the same icon as in the non-editing state in the editing state. When **symbolEditIconStyle** is also set, only the symbol edit icon is displayed and **editIcon** does not take effect.

Default value: empty string, which means no custom edit icon is displayed in the editing state.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-editIcon?: ResourceStr--><!--Device-NodeParamV2-editIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon used to customize the default icon of the node. Pass this parameter when a custom icon needs to be specified for the node. If it is not passed, the node displays the system default icon. When **symbolIconStyle** is also set, only the symbol icon is displayed and **icon** does not take effect.

Default value: empty string, which means no custom icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-icon?: ResourceStr--><!--Device-NodeParamV2-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isFolder

```TypeScript
isFolder?: boolean
```

Whether the node is a folder. The value **true** indicates a directory node that can contain child nodes (used when a parent node that can be expanded is required); the value **false** indicates a leaf node that cannot contain child nodes (used when a non-expandable terminal node is required). If this parameter is not passed, the default value **false** (leaf node) is used.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-isFolder?: boolean--><!--Device-NodeParamV2-isFolder?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

Parent node ID.

Value range: greater than or equal to -1.

Default value: **-1**, which is the root node ID. If the value is less than -1, the node is invalid and is not displayed in the tree view.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-parentNodeId?: number--><!--Device-NodeParamV2-parentNodeId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Primary title.

Default value: empty string, which means no primary title is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-primaryTitle?: ResourceStr--><!--Device-NodeParamV2-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Secondary title.

Default value: empty string, which means no secondary title is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-secondaryTitle?: ResourceStr--><!--Device-NodeParamV2-secondaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIcon

```TypeScript
selectedIcon?: ResourceStr
```

Selected icon used to customize the icon displayed when the node is selected. Pass this parameter when an icon different from the default state needs to be displayed in the node selection state. If it is not passed, the node displays the same icon as in the unselected state after being selected. When **symbolSelectedIconStyle** is also set, only the symbol selected icon is displayed and **selectedIcon** does not take effect.

Default value: empty string, which means no custom selected icon is displayed when the node is selected.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-selectedIcon?: ResourceStr--><!--Device-NodeParamV2-selectedIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolEditIconStyle

```TypeScript
symbolEditIconStyle?: SymbolGlyphModifier
```

Symbol edit icon style used to set the system symbol icon in the node editing state. Pass this parameter when a system symbol icon is required as the edit icon (for example, when consistency with the system style and dynamic color support are needed). If it is not passed, the node displays the same icon as in the non-editing state in the editing state. Its priority is higher than that of **editIcon**. When both **symbolEditIconStyle** and **editIcon** are set, only the symbol edit icon is displayed.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-symbolEditIconStyle?: SymbolGlyphModifier--><!--Device-NodeParamV2-symbolEditIconStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIconStyle

```TypeScript
symbolIconStyle?: SymbolGlyphModifier
```

Symbol icon style used to set the system symbol icon. Pass this parameter when a system symbol icon is required (for example, when consistency with the system style and dynamic color support are needed). If it is not passed, the icon specified by the **icon** parameter is used. Its display priority is higher than that of icon. When both **symbolIconStyle** and **icon** are set, only the symbol icon is displayed.

Default value: **undefined**, which means no Symbol icon is displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-symbolIconStyle?: SymbolGlyphModifier--><!--Device-NodeParamV2-symbolIconStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolSelectedIconStyle

```TypeScript
symbolSelectedIconStyle?: SymbolGlyphModifier
```

Symbol selected icon style used to set the system Symbol icon when the node is selected. Pass this parameter when a system symbol icon is required as the selected icon (for example, when consistency with the system style and dynamic color support are needed). If it is not passed, the node displays the same icon as in the unselected state after being selected. Its priority is higher than that of **selectedIcon**. When both **symbolSelectedIconStyle** and **selectedIcon** are set, only the symbol selected icon is displayed.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-NodeParamV2-symbolSelectedIconStyle?: SymbolGlyphModifier--><!--Device-NodeParamV2-symbolSelectedIconStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
