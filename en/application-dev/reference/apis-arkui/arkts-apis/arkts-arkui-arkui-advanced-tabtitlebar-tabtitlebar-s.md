# TabTitleBar

```TypeScript
export declare struct TabTitleBar
```

The **TabTitleBar** component is a tab title bar used to switch between tabs pages. It is applicable only to level-1 pages.

> **NOTE:** 
> 
> - If the **TabTitleBar** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **TabTitleBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **TabTitleBar** component.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct TabTitleBar--><!--Device-unnamed-export declare struct TabTitleBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { TabTitleBar, TabTitleBarMenuItem, TabTitleBarTabItem } from '@kit.ArkUI';
```

## swiperContent

```TypeScript
swiperContent: () => void
```

Constructor for page content pertaining to the tab list.

**Since:** 10

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBar-swiperContent: () => void--><!--Device-TabTitleBar-swiperContent: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItems

```TypeScript
menuItems?: Array<TabTitleBarMenuItem>
```

List of menu items on the right of the title bar.

**Type:** Array&lt;[TabTitleBarMenuItem](arkts-arkui-arkui-advanced-tabtitlebar-tabtitlebarmenuitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBar-menuItems?: Array<TabTitleBarMenuItem>--><!--Device-TabTitleBar-menuItems?: Array<TabTitleBarMenuItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tabItems

```TypeScript
tabItems: Array<TabTitleBarTabItem>
```

List of tab items on the left of the title bar.

**Type:** Array&lt;[TabTitleBarTabItem](arkts-arkui-arkui-advanced-tabtitlebar-tabtitlebartabitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBar-tabItems: Array<TabTitleBarTabItem>--><!--Device-TabTitleBar-tabItems: Array<TabTitleBarTabItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
