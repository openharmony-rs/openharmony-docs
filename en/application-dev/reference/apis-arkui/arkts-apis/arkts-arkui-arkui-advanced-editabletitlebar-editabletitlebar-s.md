# EditableTitleBar

```TypeScript
export declare struct EditableTitleBar
```

The editable title bar is a title bar that comes with button icons, typically **Cancel** on the left and **Confirm** on the right, on a multi-select or editing page.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **EditableTitleBar** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) and [universal events](../arkts-components/arkts-arkui-common-comp.md#common) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **EditableTitleBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **EditableTitleBar** component.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## onCancel

```TypeScript
onCancel?: () => void
```

Cancel action event, which is triggered when the left button is of the Cancel type. This parameter is required to customize the return or cancel operation logic. If this parameter is not specified, clicking the button on the left does not respond.

Default value: **() =&gt; void**

Back action event, which is triggered when the button on the left side is of the Back type, since API version 12.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSave

```TypeScript
onSave?: () => void
```

Save button click event. This parameter is required to customize the save operation logic. If this parameter is not specified, clicking the button does not respond.

Default value: **() =&gt; void**

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
contentMargin?: LocalizedMargin
```

Content margin. Negative numbers are not supported.

Default value:

{start: LengthMetrics.resource(*$r('sys.float.margin_left')*), end: LengthMetrics.resource(*$r('sys.float.margin_right')*)}

**Type:** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**Default:** {start: LengthMetrics.resource($r('sys.float.margin_left')), <br> end: LengthMetrics.resource($r('sys.float.margin_right'))}

**Since:** 12

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageItem

```TypeScript
imageItem?: EditableTitleBarItem
```

A single menu item for the profile picture on the left. This parameter is required to display a profile picture on the left side of the title bar. If this parameter is not passed, the default value is used and no profile picture is displayed.

Default value: **undefined**

Note: Accessibility properties are not supported.

**Type:** [EditableTitleBarItem](arkts-arkui-editabletitlebaritem-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isSaveIconRequired

```TypeScript
isSaveIconRequired: boolean
```

Whether the save button on the right is required.

Default value: **true**, indicating that the save button on the right is required.

**NOTE:** 

If not decorated by @Require, this parameter is not subject to mandatory validation during construction.

**Type:** boolean

**Default:** true

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leftIconDefaultFocus

```TypeScript
leftIconDefaultFocus?: boolean
```

Whether the left icon is the default focus.

Default value: **false**, indicating that the left icon is not the default focus.

**Type:** boolean

**Default:** { false }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leftIconStyle

```TypeScript
leftIconStyle: EditableLeftIconType
```

Type of the icon on the left.

Default value: **EditableLeftIconType.Back**

**Type:** [EditableLeftIconType](arkts-arkui-arkui-advanced-editabletitlebar-editablelefticontype-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<EditableTitleBarMenuItem>
```

List of menu items on the right. This parameter is required to display custom buttons on the right of the title bar. If this parameter is not passed, the default value is used, and no menu item list is displayed on the right.

Default value: **undefined**

**Type:** Array&lt;[EditableTitleBarMenuItem](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebarmenuitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: EditableTitleBarOptions
```

Title style.

Default value:

{

safeAreaTypes: [SafeAreaType.SYSTEM],

safeAreaEdges: [SafeAreaEdge.TOP],

backgroundColor: '#00000000'

}

**NOTE:** 

If not decorated by @Require, this parameter is not subject to mandatory validation during construction.

**Type:** [EditableTitleBarOptions](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebaroptions-i.md)

**Default:** {expandSafeAreaTypes: SafeAreaType.SYSTEM, expandSafeAreaEdges: SafeAreaEdge.TOP}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## saveIconDefaultFocus

```TypeScript
saveIconDefaultFocus?: boolean
```

Whether the save icon is the default focus.

Default value: **false**, indicating that the save icon is not the default focus.

**Type:** boolean

**Default:** { false }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Subtitle. This parameter is required to display a subtitle below the title bar. If this parameter is not passed, the default value is used and no subtitle is displayed.

Default value: **''**, indicating that the subtitle is empty.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Title.

Default value: **''**, indicating that the title is empty.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
