# UIInspector

```TypeScript
export class UIInspector
```

Provides the capability to register callbacks for component layout and component draw-to-display completion notifications. "Draw-to-display" means that the drawing commands of the node are sent to the graphics service and have been successfully displayed. For example, you can obtain the precise component size after layout is complete, or perform operations such as screenshot capture or animation synchronization after draw-to-display is complete. This is suitable for scenarios where precise awareness of component layout and drawing timing is required.

**Since:** 10

<!--Device-unnamed-export class UIInspector--><!--Device-unnamed-export class UIInspector-End-->

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

Registers callbacks for component layout and component draw-to-display completion notifications. For example, you can obtain the precise component size after layout is complete, or perform operations such as screenshot capture or animation synchronization after draw-to-display is complete.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-UIInspector-createComponentObserver(id: string): inspector.ComponentObserver--><!--Device-UIInspector-createComponentObserver(id: string): inspector.ComponentObserver-End-->

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

## createComponentObserver

```TypeScript
createComponentObserver(id: string | number): inspector.ComponentObserver
```

Registers callbacks for component layout and component draw-to-display completion notifications. "Draw-to-display"means that the drawing commands of the node are sent to the graphics service and have been successfully displayed. For example, you can obtain the precise component size after layout is complete, or perform operations such as screenshot capture or animation synchronization after draw-to-display is complete. <br>Compared with createComponentObserver, this API additionally supports the input of **UniqueID** (the unique ID <br>allocated by the system to a node).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-UIInspector-createComponentObserver(id: string | number): inspector.ComponentObserver--><!--Device-UIInspector-createComponentObserver(id: string | number): inspector.ComponentObserver-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string &#124; number | Yes | When the type is string, this parameter specifies the component ID, which is set through the universal attribute [id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) or [key](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#key). When using a component ID to create a listener handle, ensure that the component corresponding to the ID already exists; otherwise, the listener will not take effect. When the type is number, this parameter specifies the UniqueID, which is a unique identifier assigned by the system to a node and can be obtained through [getUniqueId](arkts-arkui-framenode-c.md#getuniqueid). When using a UniqueID to create a listener handle, ensure that the node corresponding to the UniqueID already exists; otherwise, the listener will not take effect. The value range of the number type is an integer from 1 to 2147483647. |

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
