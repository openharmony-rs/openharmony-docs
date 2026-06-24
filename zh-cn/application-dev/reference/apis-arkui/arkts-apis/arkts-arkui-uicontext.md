# @ohos.arkui.UIContext

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BackPressActionProposal](arkts-arkui-backpressactionproposal-c.md) | 智慧手势返回动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，设置返回值<br/>[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md#GestureHandlingResolution)的selectedProposal为该类型对象，会返回上一页面。<br/> |
| [BaseGestureHandlingProposal](arkts-arkui-basegesturehandlingproposal-c.md) | 智慧手势处理基类。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，其回调参数类型为具体的子类类型实例。<br/> |
| [ClickActionProposal](arkts-arkui-clickactionproposal-c.md) | 智慧手势点击动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，设置返回值<br/>[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md#GestureHandlingResolution)的selectedProposal为该类型对象，会触发目标组件的点击操作。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 该动作处理遵循“先选中，再点击”的处理语义。<br/>&gt;<br/>&gt; - 当目标节点尚未被选中时，本次处理会优先建立选中态，而不会立即触发点击。<br/> |
| [ComponentSnapshot](arkts-arkui-componentsnapshot-c.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Class首批接口从API version 12开始支持。<br/>&gt;<br/>&gt; - 以下API需先使用UIContext中的[getComponentSnapshot()](arkts-arkui-uicontext-c.md#getComponentSnapshot-1)方法获取ComponentSnapshot对象，再通过此实例调用对应方法。<br/>&gt;<br/>&gt; - 缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的还是图形变换前的效果。<br/> |
| <!--DelRow-->[ComponentSnapshot](arkts-arkui-componentsnapshot-c-sys.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Class首批接口从API version 12开始支持。<br/>&gt;<br/>&gt; - 以下API需先使用UIContext中的[getComponentSnapshot()](arkts-arkui-uicontext-c.md#getComponentSnapshot-1)方法获取ComponentSnapshot对象，再通过此实例调用对应方法。<br/>&gt;<br/>&gt; - 缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的还是图形变换前的效果。<br/> |
| [ComponentUtils](arkts-arkui-componentutils-c.md) | 提供获取组件绘制区域坐标和大小的能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Class首批接口从API version 10开始支持。<br/>&gt;<br/>&gt; - 以下API需先使用UIContext中的[getComponentUtils()](arkts-arkui-uicontext-c.md#getComponentUtils-1)方法获取到ComponentUtils对象，再通过该对象调用对应方法。<br/> |
| [ContextMenuController](arkts-arkui-contextmenucontroller-c.md) | 提供控制菜单关闭的能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Class首批接口从API version 12开始支持。<br/><br/>&gt; - 以下API需先使用UIContext中的[getContextMenuController()](arkts-arkui-uicontext-c.md#getContextMenuController-1)方法获取<br/>&gt; ContextMenuController实例，再通过此实例调用对应方法。<br/> |
| [CursorController](arkts-arkui-cursorcontroller-c.md) | 提供光标样式设置的能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Class首批接口从API version 12开始支持。<br/>&gt;<br/>&gt; - 以下API需先使用UIContext中的[getCursorController()](arkts-arkui-uicontext-c.md#getCursorController-1)方法获取CursorController实例，再通过此实例调用对应方法。<br/> |
| [DragController](arkts-arkui-dragcontroller-c.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 以下API需先使用UIContext中的[getDragController()](arkts-arkui-uicontext-c.md#getDragController-1)方法获取DragController实例，再通过此实例调用对应方法。<br/> |
| <!--DelRow-->[DragController](arkts-arkui-dragcontroller-c-sys.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 以下API需先使用UIContext中的[getDragController()](arkts-arkui-uicontext-c.md#getDragController-1)方法获取DragController实例，再通过此实例调用对应方法。<br/> |
| [DynamicSyncScene](arkts-arkui-dynamicsyncscene-c.md) | Represents a dynamic synchronization scene.<br/> |
| [FocusController](arkts-arkui-focuscontroller-c.md) | 提供控制焦点的能力，如清除、移动和激活焦点等功能。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 以下API需先使用UIContext中的[getFocusController()](arkts-arkui-uicontext-c.md#getFocusController-1)方法获取FocusController实例，再通过该实例调用对应方法。<br/> |
| [Font](arkts-arkui-font-c.md) | class Font<br/><br/>&lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;:<br/>&lt;br&gt;You must first use getFont() in UIContext to obtain a Font instance,<br/>and then call the APIs using the obtained instance.<br/>&lt;/p&gt;<br/> |
| [FrameCallback](arkts-arkui-framecallback-c.md) | 用于设置下一帧渲染时需要执行的任务。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 以下API需要配合[UIContext](arkts-arkui-uicontext.md)中的[postFrameCallback](arkts-arkui-uicontext-c.md#postFrameCallback-1)和<br/>&gt; [postDelayedFrameCallback](arkts-arkui-uicontext-c.md#postDelayedFrameCallback-1)使用。开发者需要继承该类并重写<br/>&gt; [onFrame](arkts-arkui-framecallback-c.md#onFrame-1)或[onIdle](arkts-arkui-framecallback-c.md#onIdle-1)方法，实现具体的业务逻辑。<br/> |
| [GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md) | 智慧手势处理结果声明类。<br/> |
| [Magnifier](arkts-arkui-magnifier-c.md) | 提供控制放大镜的能力。<br/> |
| [MarqueeDynamicSyncScene](arkts-arkui-marqueedynamicsyncscene-c.md) | Represents a dynamic synchronization scene of Marquee.<br/> |
| [MeasureUtils](arkts-arkui-measureutils-c.md) | class MeasureUtils<br/><br/>&lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;:<br/>&lt;br&gt;You must first use getMeasureUtils() in UIContext to obtain a MeasureUtils instance,<br/>and then call the APIs using the obtained instance.<br/>&lt;/p&gt;<br/> |
| [MediaQuery](arkts-arkui-mediaquery-c.md) | class MediaQuery<br/> |
| [NoneActionProposal](arkts-arkui-noneactionproposal-c.md) | 智慧手势空动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，设置返回值<br/>[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md#GestureHandlingResolution)的selectedProposal为该类型对象，不会触发任何动作。<br/> |
| [OverlayManager](arkts-arkui-overlaymanager-c.md) | 提供绘制浮层的能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本Class首批接口从API version 12开始支持。<br/><br/>&gt; - 以下API需先使用UIContext中的[getOverlayManager()](arkts-arkui-uicontext-c.md#getOverlayManager-1)方法获取到OverlayManager对象，再通过该对象调用对应方法。<br/>&gt;<br/>&gt; - OverlayManager上节点的层级在Page页面层级之上，在Dialog、Popup、Menu、BindSheet、BindContentCover和Toast等之下。<br/>&gt;<br/>&gt; - OverlayManager上节点安全区域内外的绘制方式与Page一致，键盘避让方式与Page一致。<br/>&gt;<br/>&gt; - 与OverlayManager相关的属性推荐采用AppStorage来进行应用全局存储，以免切换页面后属性值发生变化从而导致业务错误。<br/> |
| [PageSwitchActionProposal](arkts-arkui-pageswitchactionproposal-c.md) | 智慧手势翻页动作处理，默认方向为向前翻页，包括向右和向下。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，设置返回值<br/>[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md#GestureHandlingResolution)的selectedProposal为该类型对象，会触发目标组件的翻页操作。<br/> |
| [PromptAction](arkts-arkui-promptaction-c.md) | 创建并显示即时反馈、对话框、操作菜单以及自定义弹窗。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。<br/>&gt;<br/>&gt; - 本Class首批接口从API version 10开始支持。<br/>&gt;<br/>&gt; - 以下API需先使用UIContext中的[getPromptAction()](arkts-arkui-uicontext-c.md#getPromptAction-1)方法获取到<br/>    PromptAction对象，再通过该对象调用对应方法。<br/> |
| [ResolvedUIContext](arkts-arkui-resolveduicontext-c.md) | ResolvedUIContext实例对象。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。<br/>&gt;<br/>&gt; - ResolvedUIContext继承自[UIContext](arkts-arkui-uicontext.md)，该类对象包含[UIContext](arkts-arkui-uicontext.md)实例和<br/>&gt; [UIContext](arkts-arkui-uicontext.md)的解析策略。<br/> |
| [Router](arkts-arkui-router-c.md) | class Router<br/> |
| [ScrollActionProposal](arkts-arkui-scrollactionproposal-c.md) | 智慧手势滚动动作处理，默认方向为向前滚动，包括向右和向下。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，设置返回值<br/>[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md#GestureHandlingResolution)的selectedProposal为该类型对象，会触发目标组件的滚动操作。<br/> |
| [SelectActionProposal](arkts-arkui-selectactionproposal-c.md) | 智慧手势选中动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registerMonitor-1)接口动态自定义智慧手势行为时，设置返回值<br/>[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md#GestureHandlingResolution)的selectedProposal为该类型对象，会使目标组件被选中。<br/> |
| [SmartGestureController](arkts-arkui-smartgesturecontroller-c.md) | 提供智慧手势使能、监听、选中态控制，以及动态决策智慧手势行为的能力。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 以下API需先使用UIContext中的[getSmartGestureController()](arkts-arkui-uicontext-c.md#getSmartGestureController-1)方法获取SmartGestureController实例，<br/>&gt; 再通过该实例调用对应方法。<br/> |
| [SwiperDynamicSyncScene](arkts-arkui-swiperdynamicsyncscene-c.md) | 提供Swiper组件相关帧率的配置。<br/><br/>&gt; **说明**<br/>&gt; SwiperDynamicSyncScene继承自[DynamicSyncScene](arkts-arkui-uicontext.md)，对应Swiper的动态帧率场景。<br/> |
| [TargetedGestureProposal](arkts-arkui-targetedgestureproposal-c.md) | 带目标节点的智慧手势处理基类。<br/> |
| [TextMenuController](arkts-arkui-textmenucontroller-c.md) | class TextMenuController<br/> |
| [UIContext](arkts-arkui-uicontext-c.md) | UIContext实例对象。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。<br/>&gt;<br/>&gt; - 以下API需要通过对应的UIContext实例调用。获取UIContext分为三种方式，第一种是使用ohos.window中的<br/>&gt; [getUIContext()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10)方法获取UIContext实例，第二种是通过自定<br/>&gt; 义组件内置方法[getUIContext()](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext)获取UIContext<br/>&gt; 实例，第三种是通过UIContext类的静态方法如[getCallingScopeUIContext](arkts-arkui-uicontext-c.md#getCallingScopeUIContext-1)获取UIContext实例。本文中<br/>&gt; UIContext对象以uiContext表示。<br/> |
| <!--DelRow-->[UIContext](arkts-arkui-uicontext-c-sys.md) | UIContext实例对象。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。<br/>&gt;<br/>&gt; - 以下API需要通过对应的UIContext实例调用。获取UIContext分为三种方式，第一种是使用ohos.window中的<br/>&gt; [getUIContext()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10)方法获取UIContext实例，第二种是通过自定<br/>&gt; 义组件内置方法[getUIContext()](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext)获取UIContext<br/>&gt; 实例，第三种是通过UIContext类的静态方法如[getCallingScopeUIContext](arkts-arkui-uicontext-c.md#getCallingScopeUIContext-1)获取UIContext实例。本文中<br/>&gt; UIContext对象以uiContext表示。<br/> |
| [UIInspector](arkts-arkui-uiinspector-c.md) | class UIInspector<br/> |
| [UIObserver](arkts-arkui-uiobserver-c.md) | 提供UI组件行为变化的无感监听能力。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 以下API需先使用UIContext中的[getUIObserver()](arkts-arkui-uicontext-c.md#getUIObserver-1)方法获取到UIObserver对象，再通过该对象调用对应方法。<br/>&gt;<br/>&gt; - UIObserver仅能监听到本进程内的相关信息，不支持获取&lt;!--Del--&gt;[UIExtensionComponent](ui_extension_component)等&lt;!--DelEnd--&gt;跨进程场景的信<br/>&gt; 息。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceBar](arkts-arkui-atomicservicebar-i.md) | interface AtomicServiceBar<br/> |
| [GestureObserverConfigs](arkts-arkui-gestureobserverconfigs-i.md) | 该参数用于指定需要监听的手势回调阶段（传入空数组将无效），仅当手势触发指定阶段时才会发送通知。<br/> |
| [GestureTriggerInfo](arkts-arkui-gesturetriggerinfo-i.md) | 特定手势回调函数触发时的信息。<br/> |
| [OrderOverlayOptions](arkts-arkui-orderoverlayoptions-i.md) | 浮层的层级配置选项。<br/> |
| [OverlayManagerOptions](arkts-arkui-overlaymanageroptions-i.md) | 初始化[OverlayManager](arkts-arkui-uicontext.md)时所用参数。<br/> |
| [PageInfo](arkts-arkui-pageinfo-i.md) | Router和NavDestination等页面信息，若无对应的Router或NavDestination页面信息，则对应属性为undefined。<br/> |
| [SwiperContentInfo](arkts-arkui-swipercontentinfo-i.md) | Swiper组件的内容区信息。<br/> |
| [SwiperItemInfo](arkts-arkui-swiperiteminfo-i.md) | Swiper子组件的信息。<br/> |
| [TargetInfo](arkts-arkui-targetinfo-i.md) | 指定组件绑定的目标节点。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CustomKeyboardContinueFeature](arkts-arkui-customkeyboardcontinuefeature-e.md) | 自定义键盘接续特性的枚举。<br/> |
| [GestureActionPhase](arkts-arkui-gestureactionphase-e.md) | 这是一个枚举类型，表示要触发的手势回调阶段，对应于 gesture.d.ts 中定义的动作回调。因此，并非所有手势类型都具有以下所有阶段定义。例如，SwipeGesture 只有一个名为 onAction 的回调，因此它也只有一个枚举类型，即 WILL_START。<br/> |
| [GestureListenerType](arkts-arkui-gesturelistenertype-e.md) | 这是一个枚举类型，用于指示您要监视哪种手势。<br/> |
| [KeyboardAvoidMode](arkts-arkui-keyboardavoidmode-e.md) | Enum of KeyBoardAvoidMethodType<br/> |
| [MarqueeDynamicSyncSceneType](arkts-arkui-marqueedynamicsyncscenetype-e.md) | Marquee的动态帧率场景的类型枚举<br/> |
| [NodeRenderState](arkts-arkui-noderenderstate-e.md) | An enumeration type that identifies the current node's rendering state. The UI components used in<br/>the application are automatically managed by the system and controlled for participation in graphical<br/>rendering by either mounting them onto the render tree or removing them from it. Only nodes that<br/>participate in graphical rendering have the potential to be displayed. However, participating in<br/>rendering does not equal to the node's visibility, as there may be many occlusion scenarios in the<br/>actual implementation of the application. Nevertheless, if a node does not participate in rendering,<br/>it will definitely not be visible.<br/> |
| [ResolveStrategy](arkts-arkui-resolvestrategy-e.md) | UIContext对象的解析策略。<br/> |
| [SwiperDynamicSyncSceneType](arkts-arkui-swiperdynamicsyncscenetype-e.md) | 枚举值，表示动态帧率场景的类型。<br/> |
| [TextSelectionClearPolicy](arkts-arkui-textselectionclearpolicy-e.md) | TextSelectionClearPolicy的枚举<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 定义了用于在UIObserver中监听点击事件的回调类型。<br/> |
| [Context](arkts-arkui-context-t.md) | 当前组件所在Ability的上下文。<br/> |
| [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) | 组件属性、方法参数可使用CustomBuilderWithId类型来自定义UI描述，并且可以指定组件ID生成用户自定义组件。<br/> |
| [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 定义了用于在UIObserver中监听手势的回调类型。<br/> |
| [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 定义了用于在UIObserver中监控特定手势触发信息的回调类型。<br/> |
| [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 定义节点标识类型。对于string类型，代表指定组件id，该id通过通用属性[id](arkts-arkui-commonmethod-c.md#id-1)设置。对于number类型，<br/>代表系统分配的唯一标识的节点UniqueID，可通过[getUniqueId](arkts-arkui-framenode-c.md#getUniqueId-1)获取。<br/> |
| [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 定义了用于在UIObserver中监控某个特定节点渲染状态的回调类型。<br/> |
| [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Pan手势事件监听函数类型。<br/> |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | 光标样式。<br/> |

