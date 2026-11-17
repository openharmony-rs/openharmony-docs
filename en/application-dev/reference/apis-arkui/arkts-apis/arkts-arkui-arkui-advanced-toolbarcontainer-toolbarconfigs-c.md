# ToolBarConfigs

```TypeScript
export class ToolBarConfigs
```

工具栏的可观察配置存储，与[ToolBarParams](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarparams-i.md)对应。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export class ToolBarConfigs--><!--Device-unnamed-export class ToolBarConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(params: ToolBarParams)
```

工具栏配置ToolBarConfigs的构造函数。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-constructor(params: ToolBarParams)--><!--Device-ToolBarConfigs-constructor(params: ToolBarParams)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [ToolBarParams](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarparams-i.md) | Yes | 工具栏构造参数。 |

## advancedToolBarModifier

```TypeScript
advancedToolBarModifier: AdvancedToolBarV2Modifier
```

高级工具栏的修改器。

**Type:** [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-advancedToolBarModifier: AdvancedToolBarV2Modifier--><!--Device-ToolBarConfigs-advancedToolBarModifier: AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## callbacks

```TypeScript
callbacks?: ToolBarCallbacks
```

工具栏回调合集。

**Type:** [ToolBarCallbacks](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcallbacks-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-callbacks?: ToolBarCallbacks--><!--Device-ToolBarConfigs-callbacks?: ToolBarCallbacks-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: ToolBarController
```

工具栏控制器。

**Type:** [ToolBarController](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontroller-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-controller?: ToolBarController--><!--Device-ToolBarConfigs-controller?: ToolBarController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## floatingConfigs

```TypeScript
floatingConfigs?: ToolBarFloatingConfigs
```

高级工具栏的浮动配置。

**Type:** [ToolBarFloatingConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarfloatingconfigs-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-floatingConfigs?: ToolBarFloatingConfigs--><!--Device-ToolBarConfigs-floatingConfigs?: ToolBarFloatingConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## initialParams

```TypeScript
initialParams: ToolBarInitialParams
```

高级工具栏的初始位置。

**Type:** [ToolBarInitialParams](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarinitialparams-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-initialParams: ToolBarInitialParams--><!--Device-ToolBarConfigs-initialParams: ToolBarInitialParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarList

```TypeScript
toolBarList: AdvancedToolBarV2Item[]
```

要显示的高级工具栏项列表。

**Type:** [AdvancedToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2item-c.md)[]

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarConfigs-toolBarList: AdvancedToolBarV2Item[]--><!--Device-ToolBarConfigs-toolBarList: AdvancedToolBarV2Item[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
