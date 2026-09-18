# MultiNavigation

**MultiNavigation** is a component designed for multi-column display and routing navigation on large-screen devices.

> **NOTE:** 

> Due to the nested stack structure of **MultiNavigation**, calling APIs explicitly stated as unsupported in this
> document or APIs not listed in the supported API list (such as **getParent**, **setInterception**, and
> **pushDestination**) may lead to unpredictable issues.

> In scenarios with deep nesting, **MultiNavigation** may encounter routing animation issues.

@struct { MultiNavigation }

**Since:** 14

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SplitPolicy, MultiNavigation, MultiNavPathStack } from '@kit.ArkUI';
```

## navDestination

```TypeScript
navDestination: NavDestinationBuildFunction
```

Routing rules for loading the target page.

**Since:** 14

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onHomeShowOnTop

```TypeScript
onHomeShowOnTop?: OnHomeShowOnTopCallback
```

Callback invoked when the home page is on the top of the navigation stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onNavigationModeChange

```TypeScript
onNavigationModeChange?: OnNavigationModeChangeCallback
```

Callback invoked when the mode of the **MultiNavigation** component changes.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiStack

```TypeScript
multiStack: MultiNavPathStack
```

Navigation stack.

**Type:** [MultiNavPathStack](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md)

**Since:** 14

**Decorator:** @State

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
