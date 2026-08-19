# @ohos.arkui.UIContext

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BackPressActionProposal](arkts-arkui-arkui-uicontext-backpressactionproposal-c.md) | 智慧手势返回动作处理。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会返回上一页面。 |
| [BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md) | 智慧手势处理基类。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，其回调参数类型为具体的子类类型实例。 |
| [ClickActionProposal](arkts-arkui-arkui-uicontext-clickactionproposal-c.md) | 智慧手势点击动作处理。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的点击操作。 |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。 |
| [ComponentUtils](arkts-arkui-arkui-uicontext-componentutils-c.md) | 提供获取组件绘制区域坐标和大小的能力。 |
| [ContextMenuController](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md) | class ContextMenuController 提供控制菜单关闭的能力。 |
| [CursorController](arkts-arkui-arkui-uicontext-cursorcontroller-c.md) | 提供光标样式设置的能力。 |
| [DialogPresenter](arkts-arkui-arkui-uicontext-dialogpresenter-c.md) | 提供统一的Dialog API。 |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。 |
| [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md) | Represents a dynamic synchronization scene. |
| [FocusController](arkts-arkui-arkui-uicontext-focuscontroller-c.md) | 提供控制焦点的能力，如清除、移动和激活焦点等功能。 |
| [Font](arkts-arkui-arkui-uicontext-font-c.md) | Font用于管理自定义字体和系统字体信息，支持注册自定义字体、获取系统字体列表、查询字体详细信息等功能，适用于需要在应用中使用自定义字体或查询系统字体资源的场景。 |
| [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | 用于定义帧回调任务，可在下一帧渲染阶段或帧渲染任务结束后的空闲阶段执行。 |
| [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md) | 智慧手势处理结果声明类。 |
| [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) | 提供控制放大镜的显示与隐藏的能力，放大镜会对组件内容进行放大显示，便于查看组件细节。适用于非文本类组件（如图片）需要查看细节的场景。 |
| [MarqueeDynamicSyncScene](arkts-arkui-arkui-uicontext-marqueedynamicsyncscene-c.md) | 提供Marquee组件动态帧率的配置能力，支持在Marquee组件运行动画时动态调节帧率，优化性能和功耗，适用于需要在跑马灯场景中平衡动画流畅度和系统资源消耗的场景。 |
| [MeasureUtils](arkts-arkui-arkui-uicontext-measureutils-c.md) | MeasureUtils提供文本宽度、高度等相关计算能力，适用于文本自适应布局、多行文本截断、动态UI适配等场景。通过该类可精确计算文本尺寸，帮助开发者在布局前预判文本显示效果，避免文本溢出或布局错乱等问题。 |
| [MediaQuery](arkts-arkui-arkui-uicontext-mediaquery-c.md) | class MediaQuery |
| [NoneActionProposal](arkts-arkui-arkui-uicontext-noneactionproposal-c.md) | 智慧手势空动作处理。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，不会触发任何动作。 |
| [OverlayManager](arkts-arkui-arkui-uicontext-overlaymanager-c.md) | class OverlayManager |
| [PageSwitchActionProposal](arkts-arkui-arkui-uicontext-pageswitchactionproposal-c.md) | 智慧手势翻页动作处理，默认方向为向前翻页，包括向右和向下。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的翻页操作。 |
| [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md) | 创建并显示即时反馈、对话框、操作菜单以及自定义弹窗。 |
| [ResolvedUIContext](arkts-arkui-arkui-uicontext-resolveduicontext-c.md) | ResolvedUIContext实例对象。 |
| [Router](arkts-arkui-arkui-uicontext-router-c.md) | class Router |
| [ScrollActionProposal](arkts-arkui-arkui-uicontext-scrollactionproposal-c.md) | 智慧手势滚动动作处理，默认方向为向前滚动，包括向右和向下。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的滚动操作。 |
| [SelectActionProposal](arkts-arkui-arkui-uicontext-selectactionproposal-c.md) | 智慧手势选中动作处理。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会使目标组件被选中。 |
| [SmartGestureController](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md) | 提供智慧手势使能、监听、选中态控制，以及动态决策智慧手势行为的能力。 |
| [SwiperDynamicSyncScene](arkts-arkui-arkui-uicontext-swiperdynamicsyncscene-c.md) | 提供Swiper组件动态帧率场景的相关配置，适用于为动画过渡和手势跟手等不同交互场景设置差异化帧率范围，以兼顾流畅度和功耗。 |
| [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md) | 带目标节点的智慧手势处理基类。 |
| [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) | TextMenuController用于控制文本选择菜单的行为，支持设置菜单显示选项（如优先使用独立窗口显示）、屏蔽系统服务菜单项或指定菜单项，适用于需要自定义文本选择菜单显示方式或限制特定菜单功能的应用场景，如在特定业务场景下禁用翻译、搜索等功能。 |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | UIContext实例对象。 |
| [UIInspector](arkts-arkui-arkui-uicontext-uiinspector-c.md) | class UIInspector 提供注册组件布局和组件绘制送显完成回调通知的能力。送显指节点的绘制命令发送到图形服务并完成显示。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作，适用于需要精确感知组件布局和绘制时机的场景。 |
| [UIObserver](arkts-arkui-arkui-uicontext-uiobserver-c.md) | UIObserver提供了UI组件行为变化的无感监听能力，支持监听Navigation页面状态变化（NavDestination）、滚动事件、路由页面状态、屏幕像素密度变化、 绘制指令下发、布局完成、页面切换等多种UI组件行为。开发者可以通过该模块实现对UI组件状态的实时感知和追踪，适用于需要监控页面生命周期、处理滚动事件、 优化渲染性能等场景，帮助开发者更好地理解和管理UI组件的行为变化。无感监听是指在组件状态变化时，系统自动触发回调函数通知开发者，无需开发者手动轮询或主动查询组件状态。监听器通过注册回调函数实现，当目标组件状态改变时，系统内部的事件分发机制会调用已注册的回调函数，携带状态变化信息。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c-sys.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。 |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c-sys.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。 |
| [LuminanceSampler](arkts-arkui-arkui-uicontext-luminancesampler-c-sys.md) | 设置背景亮度取色参数、注册亮度变化监听回调、取消注册监听回调。 |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c-sys.md) | UIContext实例对象。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceBar](arkts-arkui-arkui-uicontext-atomicservicebar-i.md) | interface AtomicServiceBar |
| [GestureObserverConfigs](arkts-arkui-arkui-uicontext-gestureobserverconfigs-i.md) | 该参数用于指定需要监听的手势回调阶段（传入空数组将无效），仅当手势触发指定阶段时才会发送通知。 |
| [GestureTriggerInfo](arkts-arkui-arkui-uicontext-gesturetriggerinfo-i.md) | 特定手势回调函数触发时的信息。 |
| [OrderOverlayOptions](arkts-arkui-arkui-uicontext-orderoverlayoptions-i.md) | 使用顺序打开浮层的选项。 |
| [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | the property of OverlayManager. |
| [PageInfo](arkts-arkui-arkui-uicontext-pageinfo-i.md) | Defines the PageInfo type. The value of routerPageInfo indicates the information of the router page, or undefined if the frameNode does not have router page information. And the value of navDestinationInfo indicates the information of the navDestination, or undefined if the frameNode does not have navDestination information. |
| [SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md) | Swiper组件的内容区信息。 |
| [SwiperItemInfo](arkts-arkui-arkui-uicontext-swiperiteminfo-i.md) | Swiper子组件的信息。 |
| [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | 指定组件绑定的目标节点。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BackgroundLuminanceSamplingConfigs](arkts-arkui-arkui-uicontext-backgroundluminancesamplingconfigs-i-sys.md) | 背景取色参数配置。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CustomKeyboardContinueFeature](arkts-arkui-arkui-uicontext-customkeyboardcontinuefeature-e.md) | 自定义键盘接续特性的枚举。 |
| [GestureActionPhase](arkts-arkui-arkui-uicontext-gestureactionphase-e.md) | 此枚举类型表示手势回调触发阶段，对应gesture.d.ts中定义的动作回调，但不同手势类型支持的阶段不同（如SwipeGesture仅包含WILL_START枚举值）。 |
| [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | 此枚举类型用于指定需要监控的手势类型。 |
| [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | 配置键盘弹出时页面的避让模式。 |
| [MarqueeDynamicSyncSceneType](arkts-arkui-arkui-uicontext-marqueedynamicsyncscenetype-e.md) | Marquee的动态帧率场景的类型枚举 |
| [NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md) | An enumeration type that identifies the current node's rendering state. The UI components used in the application are automatically managed by the system and controlled for participation in graphical rendering by either mounting them onto the render tree or removing them from it. Only nodes that participate in graphical rendering have the potential to be displayed. However, participating in rendering does not equal to the node's visibility, as there may be many occlusion scenarios in the actual implementation of the application. Nevertheless, if a node does not participate in rendering, it will definitely not be visible. |
| [ResolveStrategy](arkts-arkui-arkui-uicontext-resolvestrategy-e.md) | UIContext对象的解析策略。 |
| [SwiperDynamicSyncSceneType](arkts-arkui-arkui-uicontext-swiperdynamicsyncscenetype-e.md) | 枚举值，表示动态帧率场景的类型。 |
| [TextSelectionClearPolicy](arkts-arkui-arkui-uicontext-textselectionclearpolicy-e.md) | TextSelectionClearPolicy的枚举 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 定义了用于在UIObserver中监听点击事件的回调类型。 |
| [Context](arkts-arkui-context-t.md) | 当前组件所在Ability的上下文。 |
| [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) | 组件属性、方法参数可使用CustomBuilderWithId类型来自定义UI描述，并且可以指定组件ID生成用户自定义组件。 |
| [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 定义了用于在UIObserver中监听手势的回调类型。 |
| [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 定义了用于在UIObserver中监控特定手势触发信息的回调类型。 |
| [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 定义节点标识类型。对于string类型，代表指定组件id，该id通过通用属性id设置。对于number类型， 代表系统分配的唯一标识的节点UniqueID，可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid)获取。 |
| [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 定义了用于在UIObserver中监控某个特定节点渲染状态的回调类型。 |
| [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Pan手势事件监听函数类型。 |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | 光标样式。 |

