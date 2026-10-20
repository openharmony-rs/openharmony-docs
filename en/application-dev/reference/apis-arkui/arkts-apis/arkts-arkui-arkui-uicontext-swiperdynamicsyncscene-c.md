# SwiperDynamicSyncScene

```TypeScript
export class SwiperDynamicSyncScene extends DynamicSyncScene
```

Provides frame rate configuration APIs for the **Swiper** component.

> **NOTE:** 

> - The initial APIs of this class are supported since API version 12.
> 
> - **SwiperDynamicSyncScene** inherits from [DynamicSyncScene](arkts-arkui-arkui-uicontext-uicontext-c.md) and represents the dynamic sync scene of the **Swiper** component.

**Inheritance/Implementation:** SwiperDynamicSyncScene extends [DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md)

**Since:** 12

<!--Device-unnamed-export class SwiperDynamicSyncScene extends DynamicSyncScene--><!--Device-unnamed-export class SwiperDynamicSyncScene extends DynamicSyncScene-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## type

```TypeScript
readonly type: SwiperDynamicSyncSceneType
```

Dynamic sync scene of the **Swiper** component.

**Type:** [SwiperDynamicSyncSceneType](arkts-arkui-arkui-uicontext-swiperdynamicsyncscenetype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwiperDynamicSyncScene-readonly type: SwiperDynamicSyncSceneType--><!--Device-SwiperDynamicSyncScene-readonly type: SwiperDynamicSyncSceneType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State GESTURE: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30};
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("Animation "+ JSON.stringify(this.ANIMATION))
      Text("Gesture "+ JSON.stringify(this.GESTURE))
      Row(){
        Swiper() {
          Text('one')
          Text('two')
          Text('three')
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(()=>{
          let scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
          if (scenes) {
            this.scenes = scenes;
          }
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scene: SwiperDynamicSyncScene) => {

            if (scene.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scene.setFrameRateRange(this.ANIMATION);
            }

            if (scene.type == SwiperDynamicSyncSceneType.GESTURE) {
              scene.setFrameRateRange(this.GESTURE);
            }
          });
        })
    }
  }
}
```
