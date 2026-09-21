# ComponentUtils

```TypeScript
export class ComponentUtils
```

Provides API for obtaining the coordinates and size of the drawing area of a component.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 10.
> 
> - In the following API examples, you must first use [getComponentUtils()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentutils) in
> **UIContext** to obtain a **ComponentUtils** instance, and then call the APIs using the obtained instance.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## getRectangleById

```TypeScript
getRectangleById(id: string): componentUtils.ComponentInfo
```

Obtains the size, position, translation, scaling, rotation, and affine matrix information of the specified component.

> **NOTE:** 
> 
> This API should be called after the target component's layout is complete to obtain its size information. It is
> recommended that you use this API within [onAppear](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onappear).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Unique component ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [componentUtils.ComponentInfo](arkts-arkui-componentutils-componentinfo-i.md) | Size, position, translation, scaling, rotation, and affine matrix information of the component. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100001](../errorcode-internal.md#100001-internal-error) | UI execution context not found. |

**Examples**

```TypeScript
import { ComponentUtils } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let componentUtils: ComponentUtils = this.getUIContext().getComponentUtils();
          let componentInfo = componentUtils.getRectangleById("HelloWorld");
          let width = componentInfo.size.width; // Obtain the component width.
          let height = componentInfo.size.height; // Obtain the component height.
          let localOffsetX = componentInfo.localOffset.x; // Obtain the x-axis offset of the component relative to its parent component.
          let localOffsetY = componentInfo.localOffset.y; // Obtain the y-axis offset of the component relative to its parent component.
          console.info(`width: ${width}, height: ${height}, localOffsetX: ${localOffsetX}, localOffsetY: ${localOffsetY}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
