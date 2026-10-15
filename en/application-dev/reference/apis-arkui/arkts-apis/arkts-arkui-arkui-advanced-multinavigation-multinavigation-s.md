# MultiNavigation

```TypeScript
export declare struct MultiNavigation
```

The **MultiNavigation** component is a component that supports multi-column navigation, providing multi-layer page stack management capabilities. It uses **MultiNavPathStack** to uniformly manage the navigation stacks of different page types such as the home page, detail page, and full-screen page. It supports intelligent routing strategies such as left-to-right stack clearing, making it suitable for complex navigation scenarios on large-screen devices such as tablets and foldables, optimizing the page transition experience and improving user operation efficiency.

> **NOTE:** 
> 
> - Due to the multi-level page stack structure of **MultiNavigation** (the home page, detail page, and full-screen page each maintain their own sub-stacks, which are managed by **MultiNavPathStack**), calling APIs that are explicitly stated as unsupported in this document or APIs not listed in the supported API list (such as [getParent](../arkts-components/arkts-arkui-navigation-comp-navpathstack-c.md#getparent), [setInterception](../arkts-components/arkts-arkui-navigation-comp-navpathstack-c.md#setinterception),[pushDestination](../arkts-components/arkts-arkui-navigation-comp-navpathstack-c.md#pushdestination1), etc.) may cause unexpected issues.
> 
> - In deep nesting scenarios, **MultiNavigation** may experience abnormal routing animation effects.

@struct { MultiNavigation }

**Since:** 14

**Decorator:** @Component

<!--Device-unnamed-export declare struct MultiNavigation--><!--Device-unnamed-export declare struct MultiNavigation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SplitPolicy, MultiNavigation, MultiNavPathStack } from '@kit.ArkUI';
```

## navDestination

```TypeScript
navDestination: NavDestinationBuildFunction
```

Routing rule for loading the target page.

**Since:** 14

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavigation-navDestination: NavDestinationBuildFunction--><!--Device-MultiNavigation-navDestination: NavDestinationBuildFunction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onHomeShowOnTop

```TypeScript
onHomeShowOnTop?: OnHomeShowOnTopCallback
```

Callback invoked when the home page is at the top of the stack. If not passed in, the home page top-of-stack state change is not listened for.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavigation-onHomeShowOnTop?: OnHomeShowOnTopCallback--><!--Device-MultiNavigation-onHomeShowOnTop?: OnHomeShowOnTopCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onNavigationModeChange

```TypeScript
onNavigationModeChange?: OnNavigationModeChangeCallback
```

Callback invoked when the **MultiNavigation** mode changes. Pass in this callback when specific business logic (such as adjusting the page layout or updating the UI state) needs to be executed upon a navigation mode change. If not passed in, the navigation mode change event is not listened for, and no callback is triggered upon a navigation mode change.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavigation-onNavigationModeChange?: OnNavigationModeChangeCallback--><!--Device-MultiNavigation-onNavigationModeChange?: OnNavigationModeChangeCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiStack

```TypeScript
multiStack: MultiNavPathStack
```

Route stack.

**Type:** [MultiNavPathStack](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md)

**Since:** 14

**Decorator:** @State

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-MultiNavigation-multiStack: MultiNavPathStack--><!--Device-MultiNavigation-multiStack: MultiNavPathStack-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
