# LuminanceSampler (System API)

```TypeScript
export class LuminanceSampler
```

Sets the background luminance color picking parameters, registers the luminance change listening callback, and unregisters the listening callback.

> **NOTE:** 
> 
> In the following API examples, you must first use [getLuminanceSampler](arkts-arkui-arkui-uicontext-uicontext-c-sys.md#getluminancesampler) in
> **UIContext** to obtain a **LuminanceSampler** object, and then call the APIs using the obtained object.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## offBackgroundLuminanceChange

```TypeScript
offBackgroundLuminanceChange(samplingCallback?: Callback<number>): void
```

Unregisters the callback for listening to color picking. If no callback is specified, all listeners are canceled.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| samplingCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback to unregister. |

**Examples**

Since API version 23, the [setBackgroundLuminanceSamplingConfigs](#setbackgroundluminancesamplingconfigs), [onBackgroundLuminanceChange](#onbackgroundluminancechange), and [offBackgroundLuminanceChange](#offbackgroundluminancechange) APIs are added. This example calls these three APIs to obtain the color picker of the corresponding component, set the color picking parameters and color picking callback for the component through the color picker, and implement the custom background-color-based inversion effect through the color picking callback.

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';
import { Edges } from '@ohos.arkui.node';

@Entry
@Component
struct PagePicker {
  @State arr: string[] =
    ['#FFF7F7F7', '#FF004AAF', '#FF4169E1', '#FFA52A2A', '#FF008000', '#FFFFA500', '#FFFFC0CB', '#FF808080'];
  @State myButtonWidthStr: string = '400px';
  @State myButtonWidth: number = 400;
  @State myButtonHeightStr: string = '150px';
  @State myButtonHeight: number = 150;
  @State myColor: string = '#FFF7F7F7';
  @State myButtonFontColor: string = '#FF004AAF';

  build() {
    Row() {
      Stack() {
        Scroll() {
          Column() {
            ForEach(this.arr, (item: Color) => {
              Column()
                .width('100%')
                .height(200)
                .backgroundColor(item)
            })
            ForEach(this.arr, (item: Color) => {
              Column()
                .width('100%')
                .height(200)
                .backgroundColor(item)
            })
          }
          .width('100%')
        }
        .width('100%')
        .height('100%')

        Button('Button')
          .backgroundColor(this.myColor)
          .fontColor(this.myButtonFontColor)
          .margin({ bottom: 300 })
          .width(this.myButtonWidthStr)
          .height(this.myButtonHeightStr)
          .id("myButton")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            // Obtain the color picker.
            let luminanceSampler = uiContext.getLuminanceSampler({ id: "myButton", componentId: uniqueId });
            // Set the color picking range of the node.
            let edges: Edges<LengthMetrics> = {
              top: LengthMetrics.px(0),
              bottom: LengthMetrics.px(this.myButtonHeight),
              left: LengthMetrics.px(0),
              right: LengthMetrics.px(this.myButtonWidth)
            };

            luminanceSampler?.setBackgroundLuminanceSamplingConfigs({
              samplingInterval: 300,
              brightThreshold: 200,
              darkThreshold: 100,
              region: edges
            });
            // Trigger the color picking callback.
            let luminanceChangeCallback = (luminance: number) => {
              if (luminance > 200) {
                this.myColor = '#FF004AAF';
                this.myButtonFontColor = '#FFF7F7F7';
              } else if (luminance < 100) {
                this.myColor = '#FFF7F7F7';
                this.myButtonFontColor = '#FF004AAF';
              }
            };
            luminanceSampler?.offBackgroundLuminanceChange();
            luminanceSampler?.onBackgroundLuminanceChange(luminanceChangeCallback);
          })
      }.width('100%')
      .height('100%')
      .alignContent(Alignment.Bottom)
    }
    .height('100%')
  }
}
```

## onBackgroundLuminanceChange

```TypeScript
onBackgroundLuminanceChange(samplingCallback: Callback<number>): void
```

Registers the callback for listening to color picking.

The background luminance is divided into three ranges based on the luminance threshold and dark threshold set by the [setBackgroundLuminanceSamplingConfigs](#setbackgroundluminancesamplingconfigs) API: [0, Dark threshold], (Dark threshold, Luminance threshold], and (Luminance threshold, 255]. The callback is triggered when the background luminance range changes (or the listener callback is registered for the first time) and the interval between the current color picking and the last color picking reaches the specified interval, and the current background luminance is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| samplingCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the current background luminance.<br>Note: [offBackgroundLuminanceChange](#offbackgroundluminancechange) cannot be called in the listening callback. |

**Examples**

For details, see the example of [offBackgroundLuminanceChange](#offbackgroundluminancechange).

## setBackgroundLuminanceSamplingConfigs

```TypeScript
setBackgroundLuminanceSamplingConfigs(configs: BackgroundLuminanceSamplingConfigs): void
```

Sets the color picking parameters. If the luminance threshold is not within the specified range or the dark threshold is greater than the luminance threshold, an exception is thrown.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configs | [BackgroundLuminanceSamplingConfigs](arkts-arkui-arkui-uicontext-backgroundluminancesamplingconfigs-i-sys.md) | Yes | Color picking parameters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error.<br> 1. Incorrect parameter values. <br> 2. Incorrect parameters types. |

**Examples**

For details, see the example of [offBackgroundLuminanceChange](#offbackgroundluminancechange).
