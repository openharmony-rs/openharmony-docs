# Magnifier

```TypeScript
export class Magnifier
```

Provides the capability of displaying and hiding of the magnifier. The magnifier enlarges the component content for you to view the component details.

> **NOTE:** 
> 
> - In the following API examples, you must first use [getMagnifier()](arkts-arkui-arkui-uicontext-uicontext-c.md#getmagnifier) in **UIContext**to obtain a **Magnifier** instance, and then call the APIs using the obtained instance.
> 
> - The magnifier capability of this class does not affect that of text components. For text components, you are advised to use the built-in magnifier capability.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## bind

```TypeScript
bind(id: string): void
```

Binds the magnifier to the component with the specified ID.

> **NOTE:** 
> 
> Obtain the Magnifier instance by using the getMagnifier() method in UIContext.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Component ID, which can be set through the universal attribute [id](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) or [key](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#key). If the component ID is an empty string or no component is found based on the specified ID, the magnifier is not displayed. |

**Examples**

This example listens to the onTouch event to control the magnifier to zoom in on an image.

```TypeScript
import { Magnifier } from '@kit.ArkUI';

@Entry
@Component
struct MagnifierExample {
  private magnifier: Magnifier = this.getUIContext().getMagnifier();

  build() {
    Column() {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      Image($r('app.media.startIcon'))
        .draggable(false)
        .width(200)
        .height(200)
        .margin(50)
        .id('image')
        .onTouch((event: TouchEvent) => {
          if (event && event.sourceTool === SourceTool.Finger) {
            if (event.type === TouchType.Down) {
              this.magnifier.bind('image');
            } else if (event.type === TouchType.Move) {
              let touchX = event.touches[0].x;
              let touchY = event.touches[0].y;
              this.magnifier.show(touchX, touchY);
            } else if (event.type === TouchType.Up) {
              this.magnifier.unbind();
            } else if (event.type === TouchType.Cancel) {
              this.magnifier.unbind();
            }
          }
        })
    }
  }
}
```

## show

```TypeScript
show(x: number, y: number): void
```

Sets the position of the component content displayed by the magnifier relative to the upper left corner of the component. After the setting is successful, the magnifier displays the content centered at the coordinate point.

> **NOTE:** 
> 
> When the content of the component bound to the magnifier changes, the magnifier does not automatically update the
> displayed content. You need to call the **show** API to update the displayed content of the magnifier.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate of the component content displayed by the magnifier, relative to the component itself, in vp. If the coordinate value is greater than the component width or less than 0, the magnifier is not displayed. If the value is **undefined**, the current display status of the magnifier is retained. |
| y | number | Yes | Vertical coordinate of the component content displayed by the magnifier, relative to the component itself, in vp. If the coordinate value is greater than the component height or less than 0, the magnifier is not displayed. If the value is **undefined**, the current display status of the magnifier is retained. |

**Examples**

For details, see the [bind](#bind) example.

## unbind

```TypeScript
unbind(): void
```

Unbinds the magnifier from the current component.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

For details, see the [bind](#bind) example.
