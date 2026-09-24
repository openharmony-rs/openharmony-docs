# UIInspector

```TypeScript
export class UIInspector
```

Provides APIs for registering the component layout and drawing display completion callbacks.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## createComponentObserver

```TypeScript
createComponentObserver(id: string): inspector.ComponentObserver
```

Registers a callback for layout and drawing display completion notifications for a specific component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the target component, set using the universal attributes [id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) or [key](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#key). |

**Return value:**

| Type | Description |
| --- | --- |
| [inspector.ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | Component observer, which is used to register or unregister listeners for completion of component layout or drawing display. |

**Examples**

```TypeScript
import { inspector, UIInspector } from '@kit.ArkUI';

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text('UIInspector')
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80)
      }.width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      console.info('TEXT_ID layout complete');
    }
    let onDrawComplete: () => void = (): void => {
      console.info('TEXT_ID draw complete');
    }

    this.listener.on('layout', onLayoutComplete);
    this.listener.on('draw', onDrawComplete);

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```

<a id="createcomponentobserver-1"></a>

## createComponentObserver

```TypeScript
createComponentObserver(id: string | number): inspector.ComponentObserver
```

Registers a callback for layout and drawing display completion notifications for a specific component. <br>Display refers to the process of sending the drawing command of a node to the graphics service and completing <br>the display. Compared with createComponentObserver, this API supports the input of **UniqueID** (the unique ID <br>allocated by the system to a node).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string &#124; number | Yes | When the type is string, it indicates the ID of the specified component, set using the universal attributes [id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) or [key](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#key). <br>When the type is number, it indicates the unique ID of the node allocated by the system, obtained through <br>[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid). When using the unique ID to create a listener handle, <br>ensure that the node corresponding to the unique ID exists. Otherwise, the listener does not take effect. <br>The value of the parameter in the number type is an integer ranging from 1 to 2147483647. |

**Return value:**

| Type | Description |
| --- | --- |
| [inspector.ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | Component observer, which is used to register or unregister listeners for completion of component layout or drawing display. |

**Examples**

```TypeScript
import { inspector, UIInspector } from '@kit.ArkUI';

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text('UIInspector')
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80)
      }.width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      console.info('TEXT_ID layout complete');
    }
    let onDrawComplete: () => void = (): void => {
      console.info('TEXT_ID draw complete');
    }
    let onLayoutChildrenComplete: () => void = (): void => {
      console.info('UIInspectorExample children layout');
    }

    this.listener.on('layout', onLayoutComplete);
    this.listener.on('draw', onDrawComplete);

    let listenerForThis = this.getUIContext().getUIInspector().createComponentObserver(this.getUniqueId());
    listenerForThis.onLayoutChildren(onLayoutChildrenComplete);

    // Unregister callbacks through the handle. You should decide when to call these APIs.
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```
