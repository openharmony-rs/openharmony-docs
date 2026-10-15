# SelectTitleBar

```TypeScript
export declare struct SelectTitleBar
```

The dropdown menu title bar is a title bar component that includes a dropdown menu, supports quick switching between pages, and can be configured with a back button and right-side menu items. This component is suitable for scenarios where navigation and switching between different views or pages are required, and it supports first-level pages as well as second-level and higher-level interfaces. Using this component facilitates quick access to and switching between different content views, improving the convenience of page navigation and user experience.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **SelectTitleBar** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **SelectTitleBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SelectTitleBar** component.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct SelectTitleBar--><!--Device-unnamed-export declare struct SelectTitleBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## badgeValue

```TypeScript
badgeValue?: number
```

New event badge, which displays a count on the menu icon on the right side of the title bar.

Value range: [-2147483648, 2147483647]. If the value exceeds the range, 4294967296 is added to or subtracted from it to bring it within the range. If the value is not an integer, the decimal part is truncated, for example, 5.5 becomes 5.

**NOTE:** 

If this parameter is not passed or is less than or equal to 0, the event badge is not displayed.

The maximum number of messages is 99. If the number exceeds the maximum, only 99+ is displayed. An excessively large value is considered abnormal, and the event badge is not displayed.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBar-badgeValue?: number--><!--Device-SelectTitleBar-badgeValue?: number-End-->

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

<!--Device-SelectTitleBar-hidesBackButton?: boolean--><!--Device-SelectTitleBar-hidesBackButton?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<SelectTitleBarMenuItem>
```

List of menu items on the right side, which defines the menu items on the right side of the title bar. This parameter is passed when menu items need to be added on the right side. If not specified, the right-side menu area is not displayed.

**Type:** Array&lt;[SelectTitleBarMenuItem](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebarmenuitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBar-menuItems?: Array<SelectTitleBarMenuItem>--><!--Device-SelectTitleBar-menuItems?: Array<SelectTitleBarMenuItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onSelected

```TypeScript
onSelected?: ((index: number) => void)
```

Callback triggered when a dropdown menu item is selected. It passes the index of the selected item. This parameter is passed when specific business logic needs to be processed after a dropdown menu item is selected. If there is no specific business logic, this parameter can be omitted.

**Type:** ((index: number) =&gt; void)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBar-onSelected?: ((index: number) => void)--><!--Device-SelectTitleBar-onSelected?: ((index: number) => void)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<SelectOption>
```

Items in the dropdown menu.

**Type:** Array&lt;[SelectOption](../arkts-components/arkts-arkui-select-comp-selectoption-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBar-options: Array<SelectOption>--><!--Device-SelectTitleBar-options: Array<SelectOption>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: number
```

Index of the currently selected item.

The index of the first item is 0, and the default value is **0**.

**Type:** number

**Since:** 10

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBar-selected: number--><!--Device-SelectTitleBar-selected: number-End-->

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

<!--Device-SelectTitleBar-subtitle?: ResourceStr--><!--Device-SelectTitleBar-subtitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
