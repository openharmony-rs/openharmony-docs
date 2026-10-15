# NodeParam

```TypeScript
export interface NodeParam
```

Declare NodeParam.

**Since:** 10

<!--Device-unnamed-export interface NodeParam--><!--Device-unnamed-export interface NodeParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## container

```TypeScript
container?: () => void
```

Context menu component bound to the node, displayed when the user right-clicks the node. It must be defined through the **@Builder** function.

Default value: () =&gt; void

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-container?: () => void--><!--Device-NodeParam-container?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId?: number
```

Current child node ID.

Value range: greater than or equal to -1.

Cannot be the root node ID (i.e., cannot be -1) or **null**; otherwise, an exception is thrown. Two identical **currentNodeId** values cannot be set.

Default value: **-1**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-currentNodeId?: number--><!--Device-NodeParam-currentNodeId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## editIcon

```TypeScript
editIcon?: ResourceStr
```

Edit icon. If **symbolEditIconStyle** is also set, **symbolEditIconStyle** takes precedence.

Default value: empty string

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-editIcon?: ResourceStr--><!--Device-NodeParam-editIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon. If **symbolIconStyle** is also set, **symbolIconStyle** takes precedence.

Default value: empty string

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-icon?: ResourceStr--><!--Device-NodeParam-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isFolder

```TypeScript
isFolder?: boolean
```

Whether the node is a folder.

Default value: **false**

**true**: a folder that can contain child nodes and supports expand/collapse operations; **false**: not a folder, i.e., a leaf node.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-isFolder?: boolean--><!--Device-NodeParam-isFolder?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

ID of the parent node.

The value must be greater than or equal to -1.

Default value: -1. The root node ID is -1. If the value is less than -1, the setting does not take effect.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-parentNodeId?: number--><!--Device-NodeParam-parentNodeId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

Primary title.

The default value is an empty string.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-primaryTitle?: ResourceStr--><!--Device-NodeParam-primaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

Secondary title.

The default value is an empty string.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-secondaryTitle?: ResourceStr--><!--Device-NodeParam-secondaryTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIcon

```TypeScript
selectedIcon?: ResourceStr
```

Selected icon. If **symbolSelectedIconStyle** is also set, **symbolSelectedIconStyle** takes precedence.

Default value: empty string

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NodeParam-selectedIcon?: ResourceStr--><!--Device-NodeParam-selectedIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolEditIconStyle

```TypeScript
symbolEditIconStyle?: SymbolGlyphModifier
```

Symbol edit icon, which has a higher priority than **editIcon**.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeParam-symbolEditIconStyle?: SymbolGlyphModifier--><!--Device-NodeParam-symbolEditIconStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIconStyle

```TypeScript
symbolIconStyle?: SymbolGlyphModifier
```

Symbol icon, which has higher priority than **icon**.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeParam-symbolIconStyle?: SymbolGlyphModifier--><!--Device-NodeParam-symbolIconStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolSelectedIconStyle

```TypeScript
symbolSelectedIconStyle?: SymbolGlyphModifier
```

Symbol icon of the selected node, which has higher priority than **selectedIcon**.

Default value: **undefined**

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-NodeParam-symbolSelectedIconStyle?: SymbolGlyphModifier--><!--Device-NodeParam-symbolSelectedIconStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
