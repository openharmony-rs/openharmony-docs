# ComposeTitleBar

```TypeScript
export declare struct ComposeTitleBar
```

**ComposeTitleBar** is a standard title bar component that supports setting a title, avatar (optional), and subtitle (optional). It can be used on first-level pages, as well as second-level and higher pages to display a back button. It helps quickly build a unified-style title bar, simplifies page development, supports flexible menu item configuration and icon customization, and helps developers quickly implement navigation and operation entry points.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **ComposeTitleBar** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **ComposeTitleBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ComposeTitleBar** component.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct ComposeTitleBar--><!--Device-unnamed-export declare struct ComposeTitleBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeTitleBar, ComposeTitleBarMenuItem } from '@kit.ArkUI';
```

## item

```TypeScript
item?: ComposeTitleBarMenuItem
```

Single menu item for the left avatar. When not set, no avatar is displayed on the left side of the title bar.

**Type:** [ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBar-item?: ComposeTitleBarMenuItem--><!--Device-ComposeTitleBar-item?: ComposeTitleBarMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<ComposeTitleBarMenuItem>
```

List of menu items on the right side. When not set, no menu items are displayed on the right side of the title bar.

**Type:** Array&lt;[ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBar-menuItems?: Array<ComposeTitleBarMenuItem>--><!--Device-ComposeTitleBar-menuItems?: Array<ComposeTitleBarMenuItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Subtitle. When not set, no subtitle is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBar-subtitle?: ResourceStr--><!--Device-ComposeTitleBar-subtitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Title text of the title bar.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBar-title: ResourceStr--><!--Device-ComposeTitleBar-title: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
