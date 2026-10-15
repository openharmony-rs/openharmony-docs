# EditableTitleBarV2

```TypeScript
export declare struct EditableTitleBarV2
```

The editable title bar is suitable for multi-select or content editing screens. Generally, a cancel icon is placed on the left and a save button on the right. It supports left icon configuration, title configuration, avatar display, menu item customization, save button control, and style customization, helping developers quickly build a unified editable title bar.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of the editable title bar through this component, achieving more efficient UI refresh.

> **NOTE:** 
> 
> - This component can only be used in the stage model.
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) are set for **EditableTitleBarV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **EditableTitleBarV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **EditableTitleBarV2**.

**Since:** 26.0.0

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct EditableTitleBarV2--><!--Device-unnamed-export declare struct EditableTitleBarV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## imageItem

```TypeScript
imageItem?: EditableTitleBarItemV2
```

Menu item for the left avatar. Pass this parameter when an avatar needs to be displayed on the left side of the title bar. If not passed, the default value is used and no avatar is displayed.

Default value: **undefined**.

**Note:** The left avatar does not support accessibility attribute configuration.

**Type:** [EditableTitleBarItemV2](arkts-arkui-editabletitlebaritemv2-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarV2-imageItem?: EditableTitleBarItemV2--><!--Device-EditableTitleBarV2-imageItem?: EditableTitleBarItemV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leftIcon

```TypeScript
leftIcon?: EditableLeftIconV2
```

Left icon configuration. Pass this parameter when a back or cancel icon needs to be displayed on the left side of the title bar. If not passed, the default value is used and no left icon is displayed.

Default value: **undefined**.

**Type:** [EditableLeftIconV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarV2-leftIcon?: EditableLeftIconV2--><!--Device-EditableTitleBarV2-leftIcon?: EditableLeftIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<EditableTitleBarMenuItemV2>
```

List of menu items on the right. Pass this parameter when custom action buttons need to be displayed on the right side of the title bar. If not passed, the default value is used and no menu items are displayed on the right.

**Note:** A maximum of 3 menu items can be configured. If a save button is also configured, a maximum of 2 menu items can be configured. Menu items exceeding the quantity limit are not displayed.

Default value: **undefined**.

**Type:** Array&lt;[EditableTitleBarMenuItemV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarmenuitemv2-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarV2-menuItems?: Array<EditableTitleBarMenuItemV2>--><!--Device-EditableTitleBarV2-menuItems?: Array<EditableTitleBarMenuItemV2>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: EditableTitleBarStyleV2
```

Title bar style and layout configuration. Pass this parameter when you need to customize the title bar background, safe area, margins, and other styles. If not passed, the default value is used and the default title bar style is applied.

Default value: **new EditableTitleBarStyleV2()**.

**Type:** [EditableTitleBarStyleV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarV2-options: EditableTitleBarStyleV2--><!--Device-EditableTitleBarV2-options: EditableTitleBarStyleV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## saveButton

```TypeScript
saveButton?: EditableSaveButtonV2
```

Save button configuration. Pass this parameter when you need to control the visibility of the save button on the right side of the title bar, set its default focus, or configure the callback triggered upon saving. If not passed, the default value is used and the save button is displayed. If **menuItems** is also configured, a maximum of 2 menu items can be configured.

Default value: **undefined**, indicating that the save button is displayed.

**Type:** [EditableSaveButtonV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarV2-saveButton?: EditableSaveButtonV2--><!--Device-EditableTitleBarV2-saveButton?: EditableSaveButtonV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr | EditableTitleV2
```

Title content, which can be a string or an object. When a string is passed, only the main title is displayed. When an **EditableTitleV2** object is passed, both the main title and subtitle can be configured.

Default value: **new EditableTitleV2()**, indicating that the title content is empty.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; [EditableTitleV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarV2-title: ResourceStr | EditableTitleV2--><!--Device-EditableTitleBarV2-title: ResourceStr | EditableTitleV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
