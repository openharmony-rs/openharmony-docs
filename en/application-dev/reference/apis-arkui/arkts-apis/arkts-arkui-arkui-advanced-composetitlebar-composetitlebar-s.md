# ComposeTitleBar

```TypeScript
export declare struct ComposeTitleBar
```

**ComposeTitleBar** represents a common title bar that contains a title, subtitle (optional), and profile picture (optional). It can come with a Back button for switching between pages of different levels.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **ComposeTitleBar** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) and [universal events](../arkts-components/arkts-arkui-common-comp.md#common) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **ComposeTitleBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ComposeTitleBar** component.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeTitleBar, ComposeTitleBarMenuItem } from '@kit.ArkUI';
```

## item

```TypeScript
item?: ComposeTitleBarMenuItem
```

A single menu item for the profile picture on the left.

**Type:** [ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<ComposeTitleBarMenuItem>
```

List of menu items on the right.

**Type:** Array&lt;[ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Subtitle.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

Title.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
