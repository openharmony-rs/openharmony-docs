# ToolBar

```TypeScript
export declare struct ToolBar
```

The **Toolbar** component is used to display operation options for the current interface content, shown at the bottom of the interface. It is suitable for scenarios where quick action entry points need to be provided for users, such as copy, paste, and share operations on an editing page. A maximum of 5 entries are displayed at the bottom. Any excess entries are collapsed into a "More" item, displayed on the far right.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **ToolBar** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **ToolBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ToolBar** component.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct ToolBar--><!--Device-unnamed-export declare struct ToolBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## activateIndex

```TypeScript
activateIndex?: number
```

Index of the active item.

Default value: **-1**, indicating no active item. Values less than -1 are treated as no active item.

**Type:** number

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBar-activateIndex?: number--><!--Device-ToolBar-activateIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: TabsController
```

Toolbar controller, which cannot be used for controlling individual toolbar items.

**Type:** [TabsController](../arkts-components/arkts-arkui-tabs-comp-tabscontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBar-controller: TabsController--><!--Device-ToolBar-controller: TabsController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dividerModifier

```TypeScript
dividerModifier?: DividerModifier
```

Modifier for the toolbar header divider, which can be used to customize the divider's height, color, and other attributes.

Default value: system default value

**Type:** [DividerModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 13

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBar-dividerModifier?: DividerModifier--><!--Device-ToolBar-dividerModifier?: DividerModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarList

```TypeScript
toolBarList: ToolBarOptions
```

Toolbar list.

**Type:** [ToolBarOptions](arkts-arkui-arkui-advanced-toolbar-toolbaroptions-c.md)

**Since:** 10

**Decorator:** @ObjectLink

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBar-toolBarList: ToolBarOptions--><!--Device-ToolBar-toolBarList: ToolBarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarModifier

```TypeScript
toolBarModifier?: ToolBarModifier
```

Modifier for the toolbar, which can be used to set the toolbar's height, background color, padding (which only takes effect when there are fewer than five toolbar items), and whether to display the pressed state.

Default value:

Height of the toolbar: **56vp**

Background color: **ohos_id_toolbar_bg**

Padding: **24vp**

Whether to display the pressed state: yes

**Type:** [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md)

**Since:** 13

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBar-toolBarModifier?: ToolBarModifier--><!--Device-ToolBar-toolBarModifier?: ToolBarModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
