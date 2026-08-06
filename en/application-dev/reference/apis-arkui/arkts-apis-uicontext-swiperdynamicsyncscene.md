# Class (SwiperDynamicSyncScene)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d04563276400e6bf6dde4f753c5b0383bf91013a translatedAt=2026-08-05T03:08:15.805Z pushedAt=2026-08-05T07:24:51.837Z -->

Provides configuration for dynamic frame rate scenarios of the Swiper component. It is suitable for setting differentiated frame rate ranges for different interaction scenarios, such as animation transitions and gesture tracking, to balance smoothness and power consumption.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - **SwiperDynamicSyncScene** inherits from [DynamicSyncScene](arkts-apis-uicontext-dynamicsyncscene.md) and represents the dynamic sync scene of the **Swiper** component. Before use, you must first obtain an instance via the [requireDynamicSyncScene](arkts-apis-uicontext-uicontext.md#requiredynamicsyncscene12) method of UIContext, and then call the inherited method to set the frame rate range for the corresponding scene.

## Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                                     | Read-Only| Optional| Description                               |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| type<sup>12+</sup>      | [SwiperDynamicSyncSceneType](./arkts-apis-uicontext-e.md#swiperdynamicsyncscenetype12) | Yes  | No  | Dynamic sync scene of the **Swiper** component.            |

**Example**

```ts
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