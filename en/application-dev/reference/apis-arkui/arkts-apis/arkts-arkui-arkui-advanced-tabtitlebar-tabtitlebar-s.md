# TabTitleBar

```TypeScript
export declare struct TabTitleBar
```

**TabTitleBar** is a tab title bar component that supports linked switching between a tab list and associated content, and allows configuration of right menu items. It is suitable for scenarios where page content needs to be switched through tabs, such as top navigation bars. With flexible configuration of tabs and menu items, this component can meet various interaction requirements. It supports tab switching only on level-1 pages.

> **NOTE:** 
> 
> - This component can only be used in the stage model.
> 
> - When setting [universal attributes](../arkts-components/arkts-arkui-common-comp.md) or [universal events](../arkts-components/arkts-arkui-common-comp.md) of **TabTitleBar**, the compilation toolchain mounts them on the \_\_Common\_\_ node instead of directly applying them to the component itself, which may cause the settings to not take effect or not work as expected. Therefore, setting them is not recommended.

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

List of menu items on the right. If this parameter is not passed, the right menu items are not displayed.

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

List of tab items on the left.

**Type:** Array&lt;[TabTitleBarTabItem](arkts-arkui-arkui-advanced-tabtitlebar-tabtitlebartabitem-c.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBar-tabItems: Array<TabTitleBarTabItem>--><!--Device-TabTitleBar-tabItems: Array<TabTitleBarTabItem>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
