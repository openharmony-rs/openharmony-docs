# Click Sound Effect
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-03T03:15:30.022Z pushedAt=2026-11-13T01:06:00.075Z nl=1 -->

Sets whether to enable the default click sound effect for a component. This API is applicable to scenarios where you need to control the component click feedback sound effect or customize the playback of the click sound effect.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 24. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## enableClickSoundEffect

enableClickSoundEffect(enabled: boolean | undefined): T

Sets whether the component enables the default click sound effect. This API applies to scenarios where you need to control the component click feedback sound effect or customize the playback of the click sound effect. Whether the sound effect can be played also depends on the sound-related settings of the device. For example, the sound effect is not played in silent mode. After the default click sound effect is disabled, you can call audio-related APIs in the **onClick** callback to customize the playback of the sound effect.

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

## Examples
### Example 1: Disabling Default Click Sound Effect

This example configures the **enableClickSoundEffect** attribute to disable the default click sound effect of the component. You can call audio-related APIs in the **onClick** callback to customize the playback of the sound effect. For details about custom sound effect playback, see [SoundPool Guide for Playing Short Audio](../../../media/media/using-soundpool-for-playback.md).

Starting from API version 24, the [enableClickSoundEffect](#enableclicksoundeffect) API is added.
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
          // Play the click sound effect here. For details, see the guide on playing short audio with SoundPool.
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```