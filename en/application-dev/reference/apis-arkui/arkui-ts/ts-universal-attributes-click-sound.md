# Click Sound Effect
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can enable or disable the default click sound effect for a component.

> **NOTE**
>
>
> This API is supported since API version 24. Updates will be marked with a superscript to indicate their earliest API version.

## enableClickSoundEffect

enableClickSoundEffect(enabled: boolean | undefined): T

Sets whether to enable the default click sound effect for a component. Whether the sound can be played depends on the sound settings of the device. For example, the sound effect is not played in mute mode.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: This API can be called on TVs but has no effect on other devices.

**Parameters**

| Name| Type                                                 | Mandatory| Description                                                        |
| ------ | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enabled  | boolean&nbsp;\|&nbsp;undefined | Yes  | Whether to enable the default click sound effect for a component.<br>The value **true** indicates that the default click sound effect is enabled, and **false** indicates the opposite.<br>If the value is **undefined**, the default click sound effect is enabled.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## Example
### Example 1: Enabling the Default Click Sound Effect

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
          // Customize the sound effect. For details, see the guide of using SoundPool.
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```
