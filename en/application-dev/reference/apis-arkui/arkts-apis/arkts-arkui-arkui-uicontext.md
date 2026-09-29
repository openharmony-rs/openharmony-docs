# @ohos.arkui.UIContext

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [BackPressActionProposal](arkts-arkui-arkui-uicontext-backpressactionproposal-c.md) | Smart gesture back press action handling. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this typenavigates back to the previous page. |
| [BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md) | Base class for smart gesture handling. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, the callback parameter type is an instance of a specific subclass type. |
| [ClickActionProposal](arkts-arkui-arkui-uicontext-clickactionproposal-c.md) | Smart gesture click action handling. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this typetriggers a click operation on the target component. |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md) | Provides APIs for obtaining component snapshots, including snapshots of components that have been loaded and snapshots of components that have not been loaded yet. |
| [ComponentUtils](arkts-arkui-arkui-uicontext-componentutils-c.md) | Provides API for obtaining the coordinates and size of the drawing area of a component. |
| [ContextMenuController](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md) | Provides the capability to control the closing of context menus. |
| [CursorController](arkts-arkui-arkui-uicontext-cursorcontroller-c.md) | Provides the capability to set cursor styles. |
| [DialogPresenter](arkts-arkui-arkui-uicontext-dialogpresenter-c.md) | Provides unified dialog APIs. |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) | Provides APIs for initiating drag actions. When receiving a gesture event, such as a touch or long-press event, an application can initiate a drag action and carry drag information therein. |
| [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md) | Represents a dynamic synchronization scene. |
| [FocusController](arkts-arkui-arkui-uicontext-focuscontroller-c.md) | Provides capabilities to control focus, including features such as clearing, moving, and activating focus. |
| [Font](arkts-arkui-arkui-uicontext-font-c.md) | Provides APIs for registering custom fonts. |
| [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | Implements the API for setting the task that needs to be executed during the next frame rendering. |
| [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md) | Class for declaring the result of smart gesture handling. |
| [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) | Provides the capability of displaying and hiding of the magnifier. The magnifier enlarges the component content for you to view the component details. |
| [MarqueeDynamicSyncScene](arkts-arkui-arkui-uicontext-marqueedynamicsyncscene-c.md) | Represents a dynamic synchronization scene of Marquee. |
| [MeasureUtils](arkts-arkui-arkui-uicontext-measureutils-c.md) | Provides APIs for measuring text metrics, such as text height and width. |
| [MediaQuery](arkts-arkui-arkui-uicontext-mediaquery-c.md) | class MediaQuery |
| [NoneActionProposal](arkts-arkui-arkui-uicontext-noneactionproposal-c.md) | Smart gesture no-op action handling. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this typetriggers no action. |
| [OverlayManager](arkts-arkui-arkui-uicontext-overlaymanager-c.md) | Provides the capability to draw overlays. |
| [PageSwitchActionProposal](arkts-arkui-arkui-uicontext-pageswitchactionproposal-c.md) | Smart gesture page switch action handling. The default direction is forward page switching, including right and down. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this typetriggers a page switching operation on the target component. |
| [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md) | Provides APIs to create and display toasts, dialog boxes, action menus, and custom popups. |
| [ResolvedUIContext](arkts-arkui-arkui-uicontext-resolveduicontext-c.md) | **ResolvedUIContext** instance object. |
| [Router](arkts-arkui-arkui-uicontext-router-c.md) | Provides APIs to access pages through URLs. You can use the APIs to navigate to a specified page in an application, replace the current page with another one in the same application, and return to the previous page or a specified page. |
| [ScrollActionProposal](arkts-arkui-arkui-uicontext-scrollactionproposal-c.md) | Smart gesture scroll action handling. The default direction is forward scrolling, including right and down. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this typetriggers a scroll operation on the target component. |
| [SelectActionProposal](arkts-arkui-arkui-uicontext-selectactionproposal-c.md) | Smart gesture selection action handling. When dynamically customizing smart gesture behavior through the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor) API, setting the return value [GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)'s **selectedProposal** to an object of this type causesthe target component to be selected. |
| [SmartGestureController](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md) | Provides the capability to enable smart gestures, monitor them, control the selection state, and dynamically determine smart gesture behavior. |
| [SwiperDynamicSyncScene](arkts-arkui-arkui-uicontext-swiperdynamicsyncscene-c.md) | Provides frame rate configuration APIs for the **Swiper** component. |
| [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md) | Base class for smart gesture handling with a target node. |
| [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) | The TextMenuController class is used to control the behavior of the text selection menu. It supports setting menu display options (such as displaying in a separate window with priority), disabling system service menu items or specific menu items. It is applicable to app scenarios where the text selection menu display mode needs to be customized or specific menu functions need to be restricted, such as disabling translation, search, and other functions in specific business scenarios. |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Implements a **UIContext** instance. |
| [UIInspector](arkts-arkui-arkui-uicontext-uiinspector-c.md) | Provides APIs for registering the component layout and drawing display completion callbacks. |
| [UIObserver](arkts-arkui-arkui-uicontext-uiobserver-c.md) | Provides APIs for listening for UI component behavior changes. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c-sys.md) | Provides APIs for obtaining component snapshots, including snapshots of components that have been loaded and snapshots of components that have not been loaded yet. |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c-sys.md) | Provides APIs for initiating drag actions. When receiving a gesture event, such as a touch or long-press event, an application can initiate a drag action and carry drag information therein. |
| [LuminanceSampler](arkts-arkui-arkui-uicontext-luminancesampler-c-sys.md) | Sets the background luminance color picking parameters, registers the luminance change listening callback, and unregisters the listening callback. |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c-sys.md) | Implements a **UIContext** instance. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AtomicServiceBar](arkts-arkui-arkui-uicontext-atomicservicebar-i.md) | interface AtomicServiceBar |
| [GestureObserverConfigs](arkts-arkui-arkui-uicontext-gestureobserverconfigs-i.md) | Specifies the gesture callback phases to listen for (passing an empty array will be ineffective). Notifications are sent only when the gesture triggers the specified phases. |
| [GestureTriggerInfo](arkts-arkui-arkui-uicontext-gesturetriggerinfo-i.md) | Defines the information provided when a specific gesture callback is triggered. |
| [OrderOverlayOptions](arkts-arkui-arkui-uicontext-orderoverlayoptions-i.md) | Options for opening an overlay with order. |
| [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | Provides the parameters used for initializing [OverlayManager](arkts-arkui-arkui-uicontext-uicontext-c.md). |
| [PageInfo](arkts-arkui-arkui-uicontext-pageinfo-i.md) | Represents the page information of the router or navigation destination. If there is no related page information, **undefined** is returned. |
| [SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md) | Provides content area information of the **Swiper** component. |
| [SwiperItemInfo](arkts-arkui-arkui-uicontext-swiperiteminfo-i.md) | Provides information about **Swiper** child components. |
| [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | Specifies the target node for component binding. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BackgroundLuminanceSamplingConfigs](arkts-arkui-arkui-uicontext-backgroundluminancesamplingconfigs-i-sys.md) | Sets the background luminance sampling parameters. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | Defines the callback type for listening for click events in **UIObserver**. |
| [Context](arkts-arkui-context-t.md) | The base context of an ability or an application. It allows access to application-specific resources. |
| [CustomBuilderWithId](arkts-arkui-custombuilderwithid-t.md) | Defines a type that can be used for component attributes and method parameters to customize the UI description and generate custom components with a specific component ID. |
| [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | Defines the callback type for gesture event listeners in **UIObserver**. |
| [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | Defines the callback type for listening for specific gesture trigger information in **UIObserver**. |
| [NodeIdentity](arkts-arkui-nodeidentity-t.md) | Defines the type can be used for identiting the node, for the string type, it's the inspector id set through .[id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) attribute, and for the number type, it's the unique ID got from the FrameNode by [getUniqueId](arkts-arkui-framenode-c.md#getuniqueid) method. |
| [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | Defines the callback type for listening for the rendering state of a specific node in **UIObserver**. |
| [OnOverlayBackPressCallback](arkts-arkui-onoverlaybackpresscallback-t.md) | Defines the callback type for intercepting a back-press event on an overlay. |
| [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | Defines a callback for pan gesture events. |
| [PointerStyle](arkts-arkui-pointerstyle-t.md) | Defines the pointer style. |

### Enums

| Name | Description |
| --- | --- |
| [CustomKeyboardContinueFeature](arkts-arkui-arkui-uicontext-customkeyboardcontinuefeature-e.md) | Enum of CustomKeyboardContinueFeature |
| [GestureActionPhase](arkts-arkui-arkui-uicontext-gestureactionphase-e.md) | Enumerates triggering phases of gesture callbacks, corresponding to the action callbacks defined in **gesture.d.ts**. However, different gesture types support different phases (for example, **SwipeGesture** only includes the **WILL_START** enumerated value). |
| [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | Enumerates the types of gestures to be listened for. |
| [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | Enumerates the modes in which the layout responds when the keyboard is displayed. |
| [MarqueeDynamicSyncSceneType](arkts-arkui-arkui-uicontext-marqueedynamicsyncscenetype-e.md) | Enum of scene type for Marquee |
| [NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md) | An enumeration type that identifies the current node's rendering state. The UI components used in the application are automatically managed by the system and controlled for participation in graphical rendering by either mounting them onto the render tree or removing them from it. Only nodes that participate in graphical rendering have the potential to be displayed. However, participating in rendering does not equal to the node's visibility, as there may be many occlusion scenarios in the actual implementation of the application. Nevertheless, if a node does not participate in rendering, it will definitely not be visible. |
| [ResolveStrategy](arkts-arkui-arkui-uicontext-resolvestrategy-e.md) | Enumerates resolution strategies for **UIContext** objects. |
| [SwiperDynamicSyncSceneType](arkts-arkui-arkui-uicontext-swiperdynamicsyncscenetype-e.md) | Enum of SwiperDynamicSyncSceneType |
| [TextSelectionClearPolicy](arkts-arkui-arkui-uicontext-textselectionclearpolicy-e.md) | Enum of TextSelectionClearPolicy |

## Examples

### Example 1: Enabling Smart Gestures and Customizing Action Handling

The following example uses the [enableSmartTapAndSlideGestures](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#enablesmarttapandslidegestures) API to enable and disable smart gestures, uses the [registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor), [unregisterMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#unregistermonitor), and [clearMonitors](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#clearmonitors) APIs to register, unregister, or clear listener callbacks for custom action handling, and uses [requestSelected](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#requestselected) to select a component.

Since API version 26.0.0, enableSmartTapAndSlideGestures, registerMonitor, unregisterMonitor, clearMonitors, requestSelected, and clearSelected are added.

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
  // Customize a callback function.
  private callback = (proposal: BaseGestureHandlingProposal): GestureHandlingResolution => {
    // proposal.operateIntention indicates the underlying operation intent. The value can be TAP, SLIDE_FORWARD, or BACK_PRESS.
    // proposal.action indicates the final action to be executed. The value can be NONE, SELECT, CLICK, PAGE_FORWARD, SCROLL_FORWARD, or BACK_PRESS.
    this.hint = `Intent=${proposal.operateIntention}, Action=${proposal.action}`;

    // Consume the current smart gesture, and then rewrite the default action handling based on proposal.action.
    const resolution = new GestureHandlingResolution(true);

    // Override the action to click.
    if (proposal.action === SmartGestureAction.CLICK) {
      const node = this.getUIContext().getFrameNodeById('target_button');
      if (node) {
        resolution.selectedProposal = new ClickActionProposal(node);
      }
    } else if (proposal.action === SmartGestureAction.SELECT) { // Override as the select action.
      const node = this.getUIContext().getFrameNodeById('target_text');
      if (node) {
        resolution.selectedProposal = new SelectActionProposal(node);
      }
    } else if (proposal.action === SmartGestureAction.PAGE_FORWARD) { // Override as the page turning action.
      const node = this.getUIContext().getFrameNodeById('scroll_area');
      if (node) {
        // pageCount: The value range is [0, +∞), in pages.
        resolution.selectedProposal = new PageSwitchActionProposal(node, 1);
      }
    } else if (proposal.action === SmartGestureAction.SCROLL_FORWARD) { // Override as the scroll action.
      const node = this.getUIContext().getFrameNodeById('scroll_area');
      if (node) {
        // distance: The value range is [0, +∞), in vp.
        resolution.selectedProposal = new ScrollActionProposal(node, 180);
      }
    } else if (proposal.action === SmartGestureAction.NONE) { // Override as the empty action (no operation is performed).
      resolution.selectedProposal = new NoneActionProposal();
    } else if (proposal.action === SmartGestureAction.BACK_PRESS) { // Override as the back action.
      resolution.selectedProposal = new BackPressActionProposal();
    }

    return resolution;
  };

  build() {
    Scroll() {
      Column({ space: 12 }) {
        // Operation intent prompt.
        Text(this.hint).fontSize(13).fontColor('#666')

        // Target node: text
        Text('Text component')
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

        // Target node: button
        Button(`Button Component/Click=${this.clickCount}`)
          .id('target_button').width('100%')
          .smartGestureShortcut({ action: GestureShortcut.PRIMARY, enabled: true, selectable: true })
          .onClick(() => {
            this.clickCount += 1;
          })

        // Target node: scrollable area
        Scroll() {
          Column({ space: 6 }) {
            ForEach([0, 1, 2, 3], (item: number) => {
              Text(`Scrollable content ${item}`).width('100%').padding(10).borderRadius(8)
                .backgroundColor(item % 2 === 0 ? '#f6f8fa' : '#ffffff')
            })
          }.width('100%')
        }
        .id('scroll_area').height(120)

        Divider()

        // requestSelected/clearSelected
        Text('Selection control').fontWeight(FontWeight.Bold).fontSize(16)
        Row({ space: 8 }) {
          Button('Select').layoutWeight(1)
            .onClick(() => this.controller.requestSelected('target_button'))
          Button('Select Text').layoutWeight(1)
            .onClick(() => this.controller.requestSelected('target_text'))
          Button('Clear Selection').layoutWeight(1)
            .onClick(() => this.controller.clearSelected())
        }.width('100%')

        // registerMonitor/unregisterMonitor/clearMonitors
        Text('Monitor control').fontWeight(FontWeight.Bold).fontSize(16)
        Row({ space: 8 }) {
          Button('Register').layoutWeight(1)
            .onClick(() => this.controller.registerMonitor(this.callback))
          Button('Unregister').layoutWeight(1)
            .onClick(() => this.controller.unregisterMonitor(this.callback))
          Button('Clear').layoutWeight(1)
            .onClick(() => this.controller.clearMonitors())
        }.width('100%')

        // enableSmartTapAndSlideGestures
        Row({ space: 8 }) {
          Button('Enable Gesture').layoutWeight(1)
            .onClick(() => this.controller.enableSmartTapAndSlideGestures(true))
          Button('Disable Gesture').layoutWeight(1)
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
