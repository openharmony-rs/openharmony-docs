# Class (DynamicSyncScene)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=0db97a5b7fb8643c5f5eff515ac260c481581357 translatedAt=2026-11-02T12:42:23.130Z pushedAt=2026-11-05T07:49:49.239Z nl=1 -->

Provides frame rate configuration for components in custom scenarios, supporting the setting of the expected frame rate range and the retrieval of the current frame rate configuration. It is applicable to scenarios such as animations and gestures that require dynamic frame rate adjustment, helping optimize rendering performance and power consumption. **DynamicSyncScene** is used to synchronize the frame rate requirements of a component with the system frame rate scheduling mechanism. You can distinguish different frame rate requirements (such as animation and gesture scenes) by scene type, and the system will comprehensively determine the final frame rate based on the currently active scene.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - Before calling the following APIs, you need to use the [requireDynamicSyncScene](arkts-apis-uicontext-uicontext.md#requiredynamicsyncscene12) method in **UIContext** to obtain the **DynamicSyncScene** object and then call the corresponding API through this object.

## setFrameRateRange<sup>12+</sup>

setFrameRateRange(range: ExpectedFrameRateRange): void

Sets the expected frame rate range.

The final result is not necessarily the set frame rate; it is comprehensively determined by the system, which tries to satisfy the frame rate you set.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| range | [ExpectedFrameRateRange](../apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11)| Yes    | Expected frame rate range. **min** indicates the expected minimum frame rate, **max** indicates the expected maximum frame rate, and **expected** indicates the expected optimal frame rate. The following condition must be met: **min** ≤ **expected** ≤ **max**.<br/>Default value: **{min: 0, max: 120, expected: 120}** |

**Example**

```ts
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State GESTURE: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("Animation" + JSON.stringify(this.ANIMATION))
      Text("Gesture" + JSON.stringify(this.GESTURE))
      Row(){
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(()=>{
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
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

## getFrameRateRange<sup>12+</sup>

getFrameRateRange(): ExpectedFrameRateRange

Obtains the expected frame rate range.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                 | Description     |
| ------------------- | ------- |
| [ExpectedFrameRateRange](../apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11) | Expected frame rate range configured for the current dynamic sync scene, including the expected minimum frame rate (**min**), expected maximum frame rate (**max**), and expected optimal frame rate (**expected**). |

**Example**

```ts
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State GESTURE: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("Animation" + JSON.stringify(this.ANIMATION))
      Text("Follow-up" + JSON.stringify(this.GESTURE))
      Row(){
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(() => {
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scenes: SwiperDynamicSyncScene) => {

            if (scenes.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.ANIMATION);
              scenes.getFrameRateRange();
            }

            if (scenes.type == SwiperDynamicSyncSceneType.GESTURE) {
              scenes.setFrameRateRange(this.GESTURE);
              scenes.getFrameRateRange();
            }
          });
        })
      }
  }
}
```
