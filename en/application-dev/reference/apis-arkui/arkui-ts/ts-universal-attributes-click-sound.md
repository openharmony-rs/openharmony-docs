# Click Sound Effect
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b7d29dcb4c10e7f74b8709493d673af25bbc5983 translatedAt=2026-09-01T12:17:33.470Z -->

Sets whether to enable the default click sound effect for a component. This API is applicable to scenarios where you need to control the component click feedback sound effect or customize the playback of the click sound effect.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 24. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## enableClickSoundEffect

enableClickSoundEffect(enabled: boolean | undefined): T

Sets whether to enable the default click sound effect for a component. This API is applicable to scenarios where you need to control the component click feedback sound effect or customize the sound playback. Whether the sound can be played also depends on the sound-related settings of the device. For example, no sound effect is played in silent mode. After the default click sound effect is disabled, you can call audio-related APIs in the onClick callback to customize the sound playback.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior difference**: This API can be called normally on TVs, but has no effect on other devices.

**Parameters**

| Name| Type                                                 | Mandatory| Description                                                        |
| ------ | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enabled  | boolean&nbsp;\|&nbsp;undefined | Yes   | Whether to enable the default click sound effect for this component.<br>The value true means to enable the default click sound effect, and false means to disable the default click sound effect.<br>If the value is undefined, the default click sound effect is enabled. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## Example
### Example 1: Disabling Default Click Sound Effect

This example disables the default click sound effect by setting the **enableClickSoundEffect** attribute. You can call audio-related APIs in the **onClick** callback to customize the sound effect. For details, see [Using SoundPool to Play Short Sounds](../../../media/media/using-soundpool-for-playback.md).

The [enableClickSoundEffect](#enableclicksoundeffect) attribute is added since API version 24.
```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Click')
        .fontSize('20dp')
        .height('60')
        .width('200')
        .enableClickSoundEffect(false)
        .onClick(() => {
          // Customize the sound here. For details, see the guide on playing short audio with SoundPool.
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```