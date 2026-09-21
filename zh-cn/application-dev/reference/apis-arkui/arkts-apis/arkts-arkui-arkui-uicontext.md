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
| [BackPressActionProposal](arkts-arkui-arkui-uicontext-backpressactionproposal-c.md) | 智慧手势返回动作处理。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会返回上一页面。 |
| [BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md) | 智慧手势处理基类。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，其回调参数类型为具体的子类类型实例。 |
| [ClickActionProposal](arkts-arkui-arkui-uicontext-clickactionproposal-c.md) | 智慧手势点击动作处理。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的点击操作。 |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md) | 提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。 |
| [ComponentUtils](arkts-arkui-arkui-uicontext-componentutils-c.md) | 提供获取组件绘制区域坐标、大小、平移、缩放、旋转及仿射矩阵等属性信息的能力，适用于需要查询组件绘制区域信息的场景，帮助开发者获取组件布局结果。 |
| [ContextMenuController](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md) | 提供控制菜单关闭的能力。开发者可以通过此接口在特定场景下（如定时关闭、点击外部区域关闭等）主动关闭菜单。 |
| [CursorController](arkts-arkui-arkui-uicontext-cursorcontroller-c.md) | 提供鼠标光标样式设置的能力，支持恢复默认鼠标光标样式、设置系统鼠标光标样式以及设置自定义鼠标光标样式，适用于需要根据界面交互状态动态调整鼠标光标显示效果的场景，有助于提升界面交互提示的清晰度。 |
| [DialogPresenter](arkts-arkui-arkui-uicontext-dialogpresenter-c.md) | 提供统一的Dialog API，可创建并显示固定样式弹出框、自定义样式弹出框，并支持更新与关闭弹出框。适用于应用中需要弹出提示、确认、选择等弹出框交互的场景。 |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) | 提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。 |
| [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md) | 提供组件自定义场景下相关帧率的配置。 |
| [FocusController](arkts-arkui-arkui-uicontext-focuscontroller-c.md) | 提供控制焦点的能力，如清除、移动和激活焦点等功能，适用于需要管理页面或组件焦点状态、控制焦点流转的场景，可帮助开发者优化键盘等输入方式下的焦点交互体验。 |
| [Font](arkts-arkui-arkui-uicontext-font-c.md) | Font用于管理自定义字体和系统字体信息，支持注册自定义字体、获取系统字体列表、查询字体详细信息等功能，适用于需要在应用中使用自定义字体或查询系统字体资源的场景。 |
| [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | 用于定义帧回调任务，可在下一帧渲染阶段或帧渲染任务结束后的空闲阶段执行。 |
| [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md) | 智慧手势处理结果声明类。 |
| [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) | 提供控制放大镜的显示与隐藏的能力，放大镜会对组件内容进行放大显示，便于查看组件细节。适用于非文本类组件（如图片）需要查看细节的场景。 |
| [MarqueeDynamicSyncScene](arkts-arkui-arkui-uicontext-marqueedynamicsyncscene-c.md) | 提供Marquee组件动态帧率的配置能力，支持在Marquee组件运行动画时动态调节帧率，优化性能和功耗，适用于需要在跑马灯场景中平衡动画流畅度和系统资源消耗的场景。 |
| [MeasureUtils](arkts-arkui-arkui-uicontext-measureutils-c.md) | MeasureUtils提供文本宽度、高度等相关计算能力，适用于文本自适应布局、多行文本截断、动态UI适配等场景。通过该类可精确计算文本尺寸，帮助开发者在布局前预判文本显示效果，避免文本溢出或布局错乱等问题。 |
| [MediaQuery](arkts-arkui-arkui-uicontext-mediaquery-c.md) | class MediaQuery |
| [NoneActionProposal](arkts-arkui-arkui-uicontext-noneactionproposal-c.md) | 智慧手势空动作处理。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，不会触发任何动作。 |
| [OverlayManager](arkts-arkui-arkui-uicontext-overlaymanager-c.md) | class OverlayManager |
| [PageSwitchActionProposal](arkts-arkui-arkui-uicontext-pageswitchactionproposal-c.md) | 智慧手势翻页动作处理，默认方向为向前翻页，包括向右和向下。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的翻页操作。 |
| [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md) | 创建并显示即时反馈、对话框、操作菜单以及自定义弹窗。 |
| [ResolvedUIContext](arkts-arkui-arkui-uicontext-resolveduicontext-c.md) | ResolvedUIContext实例对象。 |
| [Router](arkts-arkui-arkui-uicontext-router-c.md) | 提供通过不同的url访问不同的页面，包括跳转到应用内的指定页面、同应用内的某个页面替换当前页面、返回上一页面或指定的页面等。Router还支持命名路由跳转、页面栈管理、参数传递、返回确认对话框等能力，适用于需要统一管理页面导航流程、处理页面间数据传递的场景，与UIContext集成使用可实现灵活的路由控制。 |
| [ScrollActionProposal](arkts-arkui-arkui-uicontext-scrollactionproposal-c.md) | 智慧手势滚动动作处理，默认方向为向前滚动，包括向右和向下。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的滚动操作。 |
| [SelectActionProposal](arkts-arkui-arkui-uicontext-selectactionproposal-c.md) | 智慧手势选中动作处理。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会使目标组件被选中。 |
| [SmartGestureController](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md) | 提供智慧手势使能、监听、选中态控制，以及动态决策智慧手势行为的能力。 |
| [SwiperDynamicSyncScene](arkts-arkui-arkui-uicontext-swiperdynamicsyncscene-c.md) | 提供Swiper组件动态帧率场景的相关配置，适用于为动画过渡和手势跟手等不同交互场景设置差异化帧率范围，以兼顾流畅度和功耗。 |
| [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md) | 带目标节点的智慧手势处理基类。 |
| [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) | TextMenuController用于控制文本选择菜单的行为，支持设置菜单显示选项（如优先使用独立窗口显示）、屏蔽系统服务菜单项或指定菜单项，适用于需要自定义文本选择菜单显示方式或限制特定菜单功能的应用场景，如在特定业务场景下禁用翻译、搜索等功能。 |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | UIContext实例对象。 |
| [UIInspector](arkts-arkui-arkui-uicontext-uiinspector-c.md) | class UIInspector |
| [UIObserver](arkts-arkui-arkui-uicontext-uiobserver-c.md) | UIObserver提供了UI组件行为变化的无感监听能力，支持监听Navigation页面状态变化（NavDestination）、滚动事件、路由页面状态、屏幕像素密度变化、绘制指令下发、布局完成、页面切换等多种UI组件行为。开发者可以通过该模块实现对UI组件状态的实时感知和追踪，适用于需要监控页面生命周期、处理滚动事件、优化渲染性能等场景，帮助开发者更好地理解和管理UI组件的行为变化。无感监听是指在组件状态变化时，系统自动触发回调函数通知开发者，无需开发者手动轮询或主动查询组件状态。监听器通过注册回调函数实现，当目标组件状态改变时，系统内部的事件分发机制会调用已注册的回调函数，携带状态变化信息。 |

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
| [GestureObserverConfigs](arkts-arkui-arkui-uicontext-gestureobserverconfigs-i.md) | 该参数用于指定需要监听的手势回调阶段（传入空数组时不监听任何手势回调阶段），仅当手势触发指定阶段时才会发送通知。 |
| [GestureTriggerInfo](arkts-arkui-arkui-uicontext-gesturetriggerinfo-i.md) | 特定手势回调函数触发时的信息。 |
| [OrderOverlayOptions](arkts-arkui-arkui-uicontext-orderoverlayoptions-i.md) | 使用顺序打开浮层的选项。 |
| [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | 初始化OverlayManager时所用参数。 |
| [PageInfo](arkts-arkui-arkui-uicontext-pageinfo-i.md) | Router和NavDestination等页面信息，若无对应的Router或NavDestination页面信息，则对应属性为undefined。 |
| [SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md) | Swiper组件的内容区信息，包含Swiper组件标识、唯一标识符及当前显示状态的子组件信息，用于获取Swiper运行时的内容区状态。 |
| [SwiperItemInfo](arkts-arkui-arkui-uicontext-swiperiteminfo-i.md) | Swiper子组件的信息，包含子组件的唯一标识符和索引，可通过SwiperContentInfo获取。 |
| [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | 指定组件绑定的目标节点。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BackgroundLuminanceSamplingConfigs](arkts-arkui-arkui-uicontext-backgroundluminancesamplingconfigs-i-sys.md) | 背景亮度采样参数配置。背景亮度采样用于定期从组件背景区域取色，根据亮度阈值判定背景的明暗程度，以支持组件自适应明暗风格等场景。 |
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
| [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 定义节点标识类型。对于string类型，代表指定组件id，该id通过通用属性[id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id)设置。对于number类型，代表系统分配的唯一标识的节点UniqueID，可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid)获取。 |
| [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 定义了用于在UIObserver中监控某个特定节点渲染状态的回调类型。 |
| [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Pan手势事件监听函数类型。 |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | 光标样式。 |

## 示例

### 示例1（启用智慧手势并自定义动作处理）

以下示例通过[enableSmartTapAndSlideGestures](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#enablesmarttapandslidegestures)接口启用、关闭智慧手势，通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)、[unregisterMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#unregistermonitor)、[clearMonitors](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#clearmonitors)接口注册、注销或清空监听回调实现自定义动作处理，以及通过[requestSelected](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#requestselected)选中组件。

从API版本26.0.0开始，新增enableSmartTapAndSlideGestures、registerMonitor、unregisterMonitor、clearMonitors、requestSelected、clearSelected。

```TypeScript
import {
  BackPressActionProposal,
  BaseGestureHandlingProposal,
  ClickActionProposal,
  GestureHandlingResolution,
  NoneActionProposal,
  PageSwitchActionProposal,
  ScrollActionProposal,
  SelectActionProposal
} from '@kit.ArkUI';

@Entry
@Component
struct SmartGestureControllerExample {
  private controller = this.getUIContext().getSmartGestureController();
  @State clickCount: number = 0;
  @State hint: string = '';
  // 自定义监听回调函数
  private callback = (proposal: BaseGestureHandlingProposal): GestureHandlingResolution => {
    // proposal.operateIntention表示底层操作意图，取值包括TAP/SLIDE_FORWARD/BACK_PRESS
    // proposal.action表示最终执行动作，取值包括NONE/SELECT/CLICK/PAGE_FORWARD/SCROLL_FORWARD/BACK_PRESS
    this.hint = `意图=${proposal.operateIntention}, 动作=${proposal.action}`;

    // 消费当前智慧手势，后续根据proposal.action改写默认动作处理。
    const resolution = new GestureHandlingResolution(true);

    // 覆盖为点击动作
    if (proposal.action === SmartGestureAction.CLICK) {
      const node = this.getUIContext().getFrameNodeById('target_button');
      if (node) {
        resolution.selectedProposal = new ClickActionProposal(node);
      }
    } else if (proposal.action === SmartGestureAction.SELECT) { // 覆盖为选中动作
      const node = this.getUIContext().getFrameNodeById('target_text');
      if (node) {
        resolution.selectedProposal = new SelectActionProposal(node);
      }
    } else if (proposal.action === SmartGestureAction.PAGE_FORWARD) { // 覆盖为翻页动作
      const node = this.getUIContext().getFrameNodeById('scroll_area');
      if (node) {
        // pageCount：取值为[0, +∞)，单位为页
        resolution.selectedProposal = new PageSwitchActionProposal(node, 1);
      }
    } else if (proposal.action === SmartGestureAction.SCROLL_FORWARD) { // 覆盖为滚动动作
      const node = this.getUIContext().getFrameNodeById('scroll_area');
      if (node) {
        // distance：取值为[0, +∞)，单位为vp
        resolution.selectedProposal = new ScrollActionProposal(node, 180);
      }
    } else if (proposal.action === SmartGestureAction.NONE) { // 覆盖为空动作（不执行任何操作）
      resolution.selectedProposal = new NoneActionProposal();
    } else if (proposal.action === SmartGestureAction.BACK_PRESS) { // 覆盖为返回动作
      resolution.selectedProposal = new BackPressActionProposal();
    }

    return resolution;
  };

  build() {
    Scroll() {
      Column({ space: 12 }) {
        // 操作意图提示
        Text(this.hint).fontSize(13).fontColor('#666')

        // 目标节点：文本
        Text('文本组件')
          .id('target_text')
          .fontSize(18)
          .width('100%')
          .padding(12)
          .borderRadius(10)
          .borderWidth(1)
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            console.info('smartGesture click is triggered');
          })

        // 目标节点：按钮
        Button(`按钮组件 / 点击=${this.clickCount}`)
          .id('target_button').width('100%')
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            this.clickCount += 1;
          })

        // 目标节点：滚动区域
        Scroll() {
          Column({ space: 6 }) {
            ForEach([0, 1, 2, 3], (item: number) => {
              Text(`滚动内容 ${item}`).width('100%').padding(10).borderRadius(8)
                .backgroundColor(item % 2 === 0 ? '#f6f8fa' : '#ffffff')
            })
          }.width('100%')
        }
        .id('scroll_area').height(120)

        Divider()

        // requestSelected/clearSelected
        Text('选中控制').fontWeight(FontWeight.Bold).fontSize(16)
        Row({ space: 8 }) {
          Button('选中按钮').layoutWeight(1)
            .onClick(() => this.controller.requestSelected('target_button'))
          Button('选中文本').layoutWeight(1)
            .onClick(() => this.controller.requestSelected('target_text'))
          Button('清空选中').layoutWeight(1)
            .onClick(() => this.controller.clearSelected())
        }.width('100%')

        // registerMonitor/unregisterMonitor/clearMonitors
        Text('Monitor 控制').fontWeight(FontWeight.Bold).fontSize(16)
        Row({ space: 8 }) {
          Button('注册').layoutWeight(1)
            .onClick(() => this.controller.registerMonitor(this.callback))
          Button('注销').layoutWeight(1)
            .onClick(() => this.controller.unregisterMonitor(this.callback))
          Button('清空').layoutWeight(1)
            .onClick(() => this.controller.clearMonitors())
        }.width('100%')

        // enableSmartTapAndSlideGestures
        Row({ space: 8 }) {
          Button('启用手势').layoutWeight(1)
            .onClick(() => this.controller.enableSmartTapAndSlideGestures(true))
          Button('禁用手势').layoutWeight(1)
            .onClick(() => this.controller.enableSmartTapAndSlideGestures(false))
        }.width('100%')
      }.width('100%')
    }
    .layoutWeight(1)
    .onAppear(() => {
      this.controller.enableSmartTapAndSlideGestures(true);
      this.controller.registerMonitor(this.callback);
    })
    .width('100%')
    .height('100%')
    .padding(12)
    .backgroundColor('#f1f3f5')
  }
}
```
