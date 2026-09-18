# SelectTitleBar

The **SelectTitleBar** component represents a drop-down menu title bar used for switching between pages of different levels (configured with the **Back** button).

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **SelectTitleBar** component has universal attributes and universal events configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **SelectTitleBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SelectTitleBar** component.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## badgeValue

```TypeScript
badgeValue?: number
```

Value for the badge.

Value range: [-2147483648, 2147483647]. If the value is out of the range, 4294967296 is added or subtracted so that the value is within the range. If the value is not an integer, it is rounded off to the nearest integer. For example, 5.5 is rounded off to 5.

Note: The badge will not be displayed if the value is less than or equal to 0.

The maximum number of messages is 99. If this limit is exceeded, only **99+** is displayed. Extremely large values are considered exceptional and will result in the badge not being displayed.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hidesBackButton

```TypeScript
hidesBackButton?: boolean
```

Whether to hide the back arrow on the left.

Default value: **false**. **true** to hide, **false** to show.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<SelectTitleBarMenuItem>
```

List of menu items on the right side of the title bar. This parameter is passed to add a list of menu items to the right side of the title bar. If this parameter is not specified, the menu area on the right is not displayed.

**Type:** Array&lt;[SelectTitleBarMenuItem](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebarmenuitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSelected

```TypeScript
onSelected?: ((index: number) => void)
```

Callback invoked when an option in the drop-down menu is selected. The index of the selected option is passed in. This parameter is passed to handle specific service logic after an option in the drop-down menu is selected. This parameter can be omitted when there is no specific service logic.

**Type:** ((index: number) =&gt; void)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<SelectOption>
```

Options in the drop-down menu.

**Type:** Array&lt;[SelectOption](../arkts-components/arkts-arkui-selectoption-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: number
```

Index of the currently selected item.

The index of the first item is 0. If this attribute is not set, the default value **0** will be used.

**Type:** number

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Subtitle, used to display supplementary information. This parameter is passed to show the subtitle. If this parameter is not specified, the subtitle area is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
