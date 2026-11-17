# ToolBarContainer

```TypeScript
export struct ToolBarContainer
```

ToolBarContainer组件，用于承载一个或多个浮动工具栏，支持停靠、安全区避让和握姿适配。

**Since:** 26.1.0

**Decorator:** @ComponentV2

<!--Device-unnamed-export struct ToolBarContainer--><!--Device-unnamed-export struct ToolBarContainer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## containerConfigs

```TypeScript
containerConfigs?: ToolBarContainerConfigs
```

容器级配置，包括停靠偏移量、安全区避让和握姿适配。

**Type:** [ToolBarContainerConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontainerconfigs-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainer-containerConfigs?: ToolBarContainerConfigs--><!--Device-ToolBarContainer-containerConfigs?: ToolBarContainerConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: Callback<void>
```

组件中显示的内容。

**Type:** Callback&lt;void&gt;

**Since:** 26.1.0

**Decorator:** @BuilderParam

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainer-content: Callback<void>--><!--Device-ToolBarContainer-content: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolbars

```TypeScript
toolbars: ToolBarConfigs[]
```

工具栏配置列表。最多支持4个工具栏，超出部分不生效。

**Type:** [ToolBarConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarconfigs-c.md)[]

**Since:** 26.1.0

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarContainer-toolbars: ToolBarConfigs[]--><!--Device-ToolBarContainer-toolbars: ToolBarConfigs[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
