# ComponentSnapshot

Provides APIs for obtaining component snapshots, including snapshots of components that have been loaded and snapshots of components that have not been loaded yet.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - In the following API examples, you must first use [getComponentSnapshot()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)in **UIContext** to obtain a **ComponentSnapshot** instance, and then call the APIs using the obtained instance.
> 
> - Transformation properties such as scaling, translation, and rotation only apply to the child components of the target component. Applying these transformation properties directly to the target component itself has no effect;the snapshot will still display the component as it appears before any transformations are applied.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## getWithRange

```TypeScript
getWithRange(start: NodeIdentity, end: NodeIdentity, isStartRect: boolean,
    options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

Captures a snapshot of the area between two specified components. This API uses a promise to return the result.

> **NOTE:** 
> 
> The components corresponding to **start** and **end** must belong to the same component tree, and the **start**
> component must be an ancestor of the **end** component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | Yes | ID of the component marking the start of the capture range. |
| end | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | Yes | ID of the component marking the end of the capture range. |
| isStartRect | boolean | Yes | Whether to use the bounding rectangle of the **start** component to determine the capture range.<br>**true**: Use the bounding rectangle of the **start** component. **false**: Use the bounding rectangle of the **end** component.<br>Default value: **true**. |
| options | [componentSnapshot.SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom snapshot configuration options. The **region** parameter is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Result of the snapshot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [100001](../errorcode-internal.md#100001-internal-error) | Invalid ID detected. |
| [160003](../errorcode-snapshot.md#160003-color-space-or-dynamic-range-mode-set-in-screenshot-options-is-not-supported) | Unsupported color space or dynamic range mode in snapshot options.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        Row() {
          Row() {
            Column() {
              Text('Text1').id('text1')
              Text('Text2').id('text2')
              Row() {
                Text('Text3').id('text3')
              }.id('root5').backgroundColor('#E4E8F0')
            }
            .width('80%')
            .height('80%')
            .justifyContent(FlexAlign.SpaceAround)
            .backgroundColor('#C1D1F0')
            .id('root4')
          }
          .width('80%')
          .height('80%')
          .justifyContent(FlexAlign.Center)
          .backgroundColor('#FFEEF0')
          .id('root3')
          .backgroundBlurStyle(BlurStyle.Thin, { colorMode: ThemeColorMode.LIGHT })
        }
        .width('80%')
        .height('80%')
        .justifyContent(FlexAlign.Center)
        .backgroundColor('#D5D5D5')
        .id('root2')
      }
      .width('50%')
      .height('50%')
      .justifyContent(FlexAlign.Center)
      .backgroundColor('#E4E8F0')
      .id('root1')

      Row() {
        Button("getWithRange")
          .onClick(() => {
            this.getUIContext()
              .getComponentSnapshot()
              .getWithRange('root2', 'root4', true)
              .then((pixmap: image.PixelMap) => {
                this.pixmap = pixmap
              })
              .catch((err: Error) => {
                console.error("error: " + err)
              })
          }).margin(10)
      }.justifyContent(FlexAlign.SpaceAround)

      Row() {
        Image(this.pixmap).width(200).height(300).border({ color: Color.Black, width: 2 }).margin(5)
      }.justifyContent(FlexAlign.SpaceAround)
    }
    .id('root')
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```
