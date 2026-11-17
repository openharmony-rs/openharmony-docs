# ToolBarFloatingConfigs

```TypeScript
export class ToolBarFloatingConfigs
```

浮动工具栏行为的可观察配置存储，与[ToolBarFloatingOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarfloatingoptions-i.md)对应。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export class ToolBarFloatingConfigs--><!--Device-unnamed-export class ToolBarFloatingConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ToolBarFloatingOptions)
```

ToolBarFloatingConfigs的构造函数。当options省略时，所有字段使用各自的默认值。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingConfigs-constructor(options?: ToolBarFloatingOptions)--><!--Device-ToolBarFloatingConfigs-constructor(options?: ToolBarFloatingOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarFloatingOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarfloatingoptions-i.md) | No | 浮动行为选项。 |

## cornerMode

```TypeScript
cornerMode?: DockCornerMode
```

角落吸附模式。MINIMIZE（默认）表示吸附到角落并跟随所在边缘；EXPAND表示保持拖拽方向。

**Type:** [DockCornerMode](arkts-arkui-arkui-advanced-toolbarcontainer-dockcornermode-e.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingConfigs-cornerMode?: DockCornerMode--><!--Device-ToolBarFloatingConfigs-cornerMode?: DockCornerMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dockAreas

```TypeScript
dockAreas?: DockArea[]
```

浮动工具栏允许停靠的区域。默认支持所有可吸附位置。

**Type:** [DockArea](arkts-arkui-arkui-advanced-toolbarcontainer-dockarea-e.md)[]

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingConfigs-dockAreas?: DockArea[]--><!--Device-ToolBarFloatingConfigs-dockAreas?: DockArea[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## draggable

```TypeScript
draggable?: boolean
```

浮动工具栏是否可拖拽。默认值：true。true表示支持拖拽，false表示禁止拖拽。

**Type:** boolean

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingConfigs-draggable?: boolean--><!--Device-ToolBarFloatingConfigs-draggable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minimizeConfigs

```TypeScript
minimizeConfigs?: ToolBarMinimizeConfigs
```

最小化配置。

**Type:** [ToolBarMinimizeConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeconfigs-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarFloatingConfigs-minimizeConfigs?: ToolBarMinimizeConfigs--><!--Device-ToolBarFloatingConfigs-minimizeConfigs?: ToolBarMinimizeConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
