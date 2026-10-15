# ComponentUtils

```TypeScript
export class ComponentUtils
```

Provides the capability to obtain attribute information of a component's drawing area, including coordinates, size, translation, scaling, rotation, and affine matrix. This is suitable for scenarios where you need to query component drawing area information, helping you access component layout results.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 10.
> 
> - In the following API examples, you must first use [getComponentUtils()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentutils) in
> **UIContext** to obtain a **ComponentUtils** instance, and then call the APIs using the obtained instance.

**Since:** 10

<!--Device-unnamed-export class ComponentUtils--><!--Device-unnamed-export class ComponentUtils-End-->

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
> This API should be called after the target component layout is complete to obtain its area size information. It is recommended to use this API in the [layout callback](arkts-arkui-arkui-inspector.md). If a component is dynamically created but not yet attached to the component tree, its measurement and layout information cannot be accessed through this API since this component has not undergone measurement and layout by the UI framework. Ensure the component is attached to the component tree before attempting to retrieve component information.
> 
> The component position returned by this API is the layout position. Some property calculations are not supported, such as position-setting properties like **offset**, **markAnchor**, **Edges**, **position** of the **LocalizedEdges** type, and graphics transformation properties like **rotate**, **translate**, **scale**, and **transform**. For an alternative, you can use [getPositionToWindowWithTransform](arkts-arkui-framenode-c.md#getpositiontowindowwithtransform) to obtain the component's position offset relative to the window, including drawing attributes.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComponentUtils-getRectangleById(id: string): componentUtils.ComponentInfo--><!--Device-ComponentUtils-getRectangleById(id: string): componentUtils.ComponentInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Unique ID of a component. Ensure that the component corresponding to the ID has been mounted to the component tree and the layout has been completed. |

**Return value:**

| Type | Description |
| --- | --- |
| [componentUtils.ComponentInfo](arkts-arkui-componentutils-componentinfo-i.md) | **ComponentInfo** object, which provides the size, position, translation, scaling, rotation, and affine matrix information of the component. |

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
