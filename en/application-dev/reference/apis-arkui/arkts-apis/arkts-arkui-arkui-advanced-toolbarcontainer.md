# @ohos.arkui.advanced.ToolBarContainer

## Modules to Import

```TypeScript
import { ToolBarState, DockArea, DockCornerMode, ToolBarSafeAreaMode, HandednessAdaptationMode, ToolBarFloatingOptions, ToolBarFloatingConfigs, ToolBarMinimizeOptions, ToolBarMinimizeConfigs, ToolBarController, ToolBarInitialParams, ToolBarParams, ToolBarConfigs, ToolBarCallbacks, ToolBarDockOffsetOptions, ToolBarSafeAreaOptions, ToolBarContainerOptions, ToolBarContainerConfigs, ToolBarContainer, ToolBarDragStateCallback, ToolBarDragOffsetCallback, ToolBarStateCallback, ToolBarDockCallback, } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ToolBarCallbacks](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcallbacks-c.md) | 用于工具栏拖拽、吸附以及状态回调的合集。 |
| [ToolBarConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarconfigs-c.md) | 工具栏的可观察配置存储，与[ToolBarParams](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarparams-i.md)对应。 |
| [ToolBarContainerConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontainerconfigs-c.md) | 工具栏容器的可观察配置存储，与[ToolBarContainerOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontaineroptions-i.md)对应。 |
| [ToolBarController](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontroller-c.md) | 用于命令式操作工具栏停靠、固定和最小化状态控制器。 |
| [ToolBarFloatingConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarfloatingconfigs-c.md) | 浮动工具栏行为的可观察配置存储，与[ToolBarFloatingOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarfloatingoptions-i.md)对应。 |
| [ToolBarMinimizeConfigs](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeconfigs-c.md) | 最小化悬浮球的可观察配置存储，与[ToolBarMinimizeOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeoptions-i.md)对应。 |

### Structs

| Name | Description |
| --- | --- |
| [ToolBarContainer](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontainer-s.md) | ToolBarContainer组件，用于承载一个或多个浮动工具栏，支持停靠、安全区避让和握姿适配。 |

### Interfaces

| Name | Description |
| --- | --- |
| [ToolBarContainerOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarcontaineroptions-i.md) | 配置工具栏容器的布局、安全区避让和握姿适配的选项。 |
| [ToolBarDockOffsetOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbardockoffsetoptions-i.md) | 配置浮动工具栏各边停靠偏移量的选项。 |
| [ToolBarFloatingOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarfloatingoptions-i.md) | 配置工具栏浮动行为的选项。 |
| [ToolBarInitialParams](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarinitialparams-i.md) | 工具栏初始位置参数，指定创建时的停靠区域、方向和状态。 |
| [ToolBarMinimizeOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarminimizeoptions-i.md) | 配置工具栏最小化悬浮球的选项。 |
| [ToolBarParams](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarparams-i.md) | 构造工具栏的参数，包括项列表、修改器、浮动配置和回调。 |
| [ToolBarSafeAreaOptions](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarsafeareaoptions-i.md) | 配置工具栏各边安全区避让模式的选项。 |

### Types

| Name | Description |
| --- | --- |
| [ToolBarDockCallback](arkts-arkui-toolbardockcallback-t.md) | 工具栏停靠到指定区域和方向时的回调。 |
| [ToolBarDragOffsetCallback](arkts-arkui-toolbardragoffsetcallback-t.md) | 相对于ToolBarContainer容器的拖拽偏移量回调。 |
| [ToolBarDragStateCallback](arkts-arkui-toolbardragstatecallback-t.md) | 工具栏的拖拽状态改变回调，拖拽开始或结束时触发。 |
| [ToolBarStateCallback](arkts-arkui-toolbarstatecallback-t.md) | 工具栏状态变化时的回调。 |

### Enums

| Name | Description |
| --- | --- |
| [DockArea](arkts-arkui-arkui-advanced-toolbarcontainer-dockarea-e.md) | 定义浮动工具栏可停靠的区域。 |
| [DockCornerMode](arkts-arkui-arkui-advanced-toolbarcontainer-dockcornermode-e.md) | 定义浮动工具栏拖拽到角落时的吸附模式。 |
| [HandednessAdaptationMode](arkts-arkui-arkui-advanced-toolbarcontainer-handednessadaptationmode-e.md) | 定义工具栏接入智感握姿模式。 |
| [ToolBarSafeAreaMode](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarsafeareamode-e.md) | 定义工具栏的安全区内边距模式。 |
| [ToolBarState](arkts-arkui-arkui-advanced-toolbarcontainer-toolbarstate-e.md) | 定义工具栏状态。 |
