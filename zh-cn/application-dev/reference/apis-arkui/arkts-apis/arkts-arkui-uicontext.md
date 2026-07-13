# @ohos.arkui.UIContext

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BackPressActionProposal](arkts-arkui-backpressactionproposal-c.md) | 智慧手势返回动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会返回上一页面。 |
| [BaseGestureHandlingProposal](arkts-arkui-basegesturehandlingproposal-c.md) | 智慧手势处理基类。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，其回调参数类型为具体的子类类型实例。 |
| [ClickActionProposal](arkts-arkui-clickactionproposal-c.md) | 智慧手势点击动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的点击操作。 |
| [ComponentSnapshot](arkts-arkui-componentsnapshot-c.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。@link UIContext#getComponentSnapshot}方法获取ComponentSnapshot对象，再通过此实例调用对应方法。&gt;&gt; - 缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的还是图形变换前的效果。 |
| [ComponentUtils](arkts-arkui-componentutils-c.md) | 提供获取组件绘制区域坐标和大小的能力。@link UIContext#getComponentUtils}方法获取到ComponentUtils对象，再通过该对象调用对应方法。 |
| [ContextMenuController](arkts-arkui-contextmenucontroller-c.md) | class ContextMenuController |
| [CursorController](arkts-arkui-cursorcontroller-c.md) | 提供光标样式设置的能力。@link UIContext#getCursorController}方法获取CursorController实例，再通过此实例调用对应方法。 |
| [DialogPresenter](arkts-arkui-dialogpresenter-c.md) | 提供统一的Dialog API。 |
| [DragController](arkts-arkui-dragcontroller-c.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。@link UIContext#getDragController}方法获取DragController实例，再通过此实例调用对应方法。 |
| [DynamicSyncScene](arkts-arkui-dynamicsyncscene-c.md) | Represents a dynamic synchronization scene. |
| [FocusController](arkts-arkui-focuscontroller-c.md) | 提供控制焦点的能力，如清除、移动和激活焦点等功能。@link UIContext#getFocusController}方法获取FocusController实例，再通过该实例调用对应方法。 |
| [Font](arkts-arkui-font-c.md) | class Font |
| [FrameCallback](arkts-arkui-framecallback-c.md) | 用于设置下一帧渲染时需要执行的任务。@link @ohos.arkui.UIContext}中的[postFrameCallback](arkts-arkui-uicontext-c.md#postframecallback-1)和&gt; [postDelayedFrameCallback](arkts-arkui-uicontext-c.md#postdelayedframecallback-1)使用。开发者需要继承该类并重写&gt; [onFrame](arkts-arkui-framecallback-c.md#onframe-1)或[onIdle](arkts-arkui-framecallback-c.md#onidle-1)方法，实现具体的业务逻辑。 |
| [GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md) | 智慧手势处理结果声明类。 |
| [Magnifier](arkts-arkui-magnifier-c.md) | 提供控制放大镜的能力。 |
| [MarqueeDynamicSyncScene](arkts-arkui-marqueedynamicsyncscene-c.md) | Represents a dynamic synchronization scene of Marquee. |
| [MeasureUtils](arkts-arkui-measureutils-c.md) | class MeasureUtils&lt;p&gt;<strong>NOTE</strong>:<br>You must first use getMeasureUtils() in UIContext to obtain a MeasureUtils instance,and then call the APIs using the obtained instance.&lt;/p&gt; |
| [MediaQuery](arkts-arkui-mediaquery-c.md) | class MediaQuery |
| [NoneActionProposal](arkts-arkui-noneactionproposal-c.md) | 智慧手势空动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，不会触发任何动作。 |
| [OverlayManager](arkts-arkui-overlaymanager-c.md) | class OverlayManager |
| [PageSwitchActionProposal](arkts-arkui-pageswitchactionproposal-c.md) | 智慧手势翻页动作处理，默认方向为向前翻页，包括向右和向下。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的翻页操作。 |
| [PromptAction](arkts-arkui-promptaction-c.md) | class PromptAction |
| [ResolvedUIContext](arkts-arkui-resolveduicontext-c.md) | ResolvedUIContext实例对象。@link @ohos.arkui.UIContext}，该类对象包含[UIContext](arkts-arkui-uicontext.md)实例和&gt; [UIContext](arkts-arkui-uicontext.md)的解析策略。 |
| [Router](arkts-arkui-router-c.md) | class Router |
| [ScrollActionProposal](arkts-arkui-scrollactionproposal-c.md) | 智慧手势滚动动作处理，默认方向为向前滚动，包括向右和向下。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的滚动操作。 |
| [SelectActionProposal](arkts-arkui-selectactionproposal-c.md) | 智慧手势选中动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会使目标组件被选中。 |
| [SmartGestureController](arkts-arkui-smartgesturecontroller-c.md) | 提供智慧手势使能、监听、选中态控制，以及动态决策智慧手势行为的能力。@link UIContext#getSmartGestureController}方法获取SmartGestureController实例，&gt; 再通过该实例调用对应方法。 |
| [SwiperDynamicSyncScene](arkts-arkui-swiperdynamicsyncscene-c.md) | 提供Swiper组件相关帧率的配置。&gt; **说明**&gt; SwiperDynamicSyncScene继承自[DynamicSyncScene](arkts-arkui-uicontext.md)，对应Swiper的动态帧率场景。 |
| [TargetedGestureProposal](arkts-arkui-targetedgestureproposal-c.md) | 带目标节点的智慧手势处理基类。 |
| [TextMenuController](arkts-arkui-textmenucontroller-c.md) | class TextMenuController |
| [UIContext](arkts-arkui-uicontext-c.md) | UIContext实例对象。@link UIContext#getCallingScopeUIContext}获取UIContext实例。本文中&gt; UIContext对象以uiContext表示。 |
| [UIInspector](arkts-arkui-uiinspector-c.md) | class UIInspector |
| [UIObserver](arkts-arkui-uiobserver-c.md) | 提供UI组件行为变化的无感监听能力。@link UIContext#getUIObserver}方法获取到UIObserver对象，再通过该对象调用对应方法。&gt;&gt; - UIObserver仅能监听到本进程内的相关信息，不支持获取&lt;!--Del--&gt;[UIExtensionComponent](ui_extension_component)等&lt;!--DelEnd--&gt;跨进程场景的信&gt; 息。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ComponentSnapshot](arkts-arkui-componentsnapshot-c-sys.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。@link UIContext#getComponentSnapshot}方法获取ComponentSnapshot对象，再通过此实例调用对应方法。&gt;&gt; - 缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的还是图形变换前的效果。 |
| [DragController](arkts-arkui-dragcontroller-c-sys.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。@link UIContext#getDragController}方法获取DragController实例，再通过此实例调用对应方法。 |
| [LuminanceSampler](arkts-arkui-luminancesampler-c-sys.md) | 设置背景亮度取色参数、注册亮度变化监听回调、取消注册监听回调。@link UIContext#getLuminanceSampler}方法获取到LuminanceSampler对象，再通过该对象调用对应方法。 |
| [UIContext](arkts-arkui-uicontext-c-sys.md) | UIContext实例对象。@link UIContext#getCallingScopeUIContext}获取UIContext实例。本文中&gt; UIContext对象以uiContext表示。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceBar](arkts-arkui-atomicservicebar-i.md) | interface AtomicServiceBar |
| [GestureObserverConfigs](arkts-arkui-gestureobserverconfigs-i.md) | 该参数用于指定需要监听的手势回调阶段（传入空数组将无效），仅当手势触发指定阶段时才会发送通知。 |
| [GestureTriggerInfo](arkts-arkui-gesturetriggerinfo-i.md) | 特定手势回调函数触发时的信息。 |
| [OrderOverlayOptions](arkts-arkui-orderoverlayoptions-i.md) | 使用顺序打开浮层的选项。 |
| [OverlayManagerOptions](arkts-arkui-overlaymanageroptions-i.md) | the property of OverlayManager. |
| [PageInfo](arkts-arkui-pageinfo-i.md) | Defines the PageInfo type.The value of routerPageInfo indicates the information of the router page, or undefined if theframeNode does not have router page information. And the value of navDestinationInfo indicatesthe information of the navDestination, or undefined if the frameNode does not have navDestinationinformation. |
| [SwiperContentInfo](arkts-arkui-swipercontentinfo-i.md) | Swiper组件的内容区信息。 |
| [SwiperItemInfo](arkts-arkui-swiperiteminfo-i.md) | Swiper子组件的信息。 |
| [TargetInfo](arkts-arkui-targetinfo-i.md) | Defines the target info. |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BackgroundLuminanceSamplingConfigs](arkts-arkui-backgroundluminancesamplingconfigs-i-sys.md) | 背景取色参数配置。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CustomKeyboardContinueFeature](arkts-arkui-customkeyboardcontinuefeature-e.md) | 自定义键盘接续特性的枚举。 |
| [GestureActionPhase](arkts-arkui-gestureactionphase-e.md) | 此枚举类型表示手势回调触发阶段，对应gesture.d.ts中定义的动作回调，但不同手势类型支持的阶段不同（如SwipeGesture仅包含WILL_START枚举值）。 |
| [GestureListenerType](arkts-arkui-gesturelistenertype-e.md) | 此枚举类型用于指定需要监控的手势类型。 |
| [KeyboardAvoidMode](arkts-arkui-keyboardavoidmode-e.md) | 配置键盘弹出时页面的避让模式。 |
| [MarqueeDynamicSyncSceneType](arkts-arkui-marqueedynamicsyncscenetype-e.md) | Marquee的动态帧率场景的类型枚举 |
| [NodeRenderState](arkts-arkui-noderenderstate-e.md) | An enumeration type that identifies the current node's rendering state. The UI components used inthe application are automatically managed by the system and controlled for participation in graphicalrendering by either mounting them onto the render tree or removing them from it. Only nodes thatparticipate in graphical rendering have the potential to be displayed. However, participating inrendering does not equal to the node's visibility, as there may be many occlusion scenarios in theactual implementation of the application. Nevertheless, if a node does not participate in rendering,it will definitely not be visible. |
| [ResolveStrategy](arkts-arkui-resolvestrategy-e.md) | UIContext对象的解析策略。 |
| [SwiperDynamicSyncSceneType](arkts-arkui-swiperdynamicsyncscenetype-e.md) | 枚举值，表示动态帧率场景的类型。 |
| [TextSelectionClearPolicy](arkts-arkui-textselectionclearpolicy-e.md) | TextSelectionClearPolicy的枚举 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 定义了用于在UIObserver中监听点击事件的回调类型。 |
| [Context](arkts-arkui-context-t.md) | 当前组件所在Ability的上下文。 |
| [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) | 组件属性、方法参数可使用CustomBuilderWithId类型来自定义UI描述，并且可以指定组件ID生成用户自定义组件。 |
| [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 定义了用于在UIObserver中监听手势的回调类型。 |
| [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 定义了用于在UIObserver中监控特定手势触发信息的回调类型。 |
| [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 定义节点标识类型。对于string类型，代表指定组件id，该id通过通用属性[id](../arkts-components/arkts-arkui-commonmethod-c.md#id-1)设置。对于number类型，代表系统分配的唯一标识的节点UniqueID，可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)获取。 |
| [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 定义了用于在UIObserver中监控某个特定节点渲染状态的回调类型。 |
| [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Pan手势事件监听函数类型。 |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | 光标样式。 |

