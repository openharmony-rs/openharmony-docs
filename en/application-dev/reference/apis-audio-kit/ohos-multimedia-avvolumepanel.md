# @ohos.multimedia.avVolumePanel (Volume Panel)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6e63a0e266900a11bfa74fe24b3b676187cc5558 translatedAt=2026-11-10T03:15:02.730Z pushedAt=2026-11-10T04:53:38.963Z nl=1 -->

The module provides the capability of displaying the system volume panel for users to adjust the volume.

An application cannot directly adjust the system volume. However, it can invoke the system volume panel for users to adjust the volume. When the user adjusts the volume, a volume prompt UI is displayed to explicitly notify the user that the system volume changes.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The sample effect is subject to the actual device. The current DevEco Studio previewer does not provide real volume display and adjustment.
> - **Device restrictions:** 
>   - On wearable devices, the component can be used to adjust the system volume, but no UI is displayed. You need to design the UI on your own.
>   - The APIs of this module are not supported on TV devices.
> - System volume bar: taking a phone as an example, the system volume bar triggered by the side buttons.
> - System volume panel: the default style of the [AVVolumePanel](#avvolumepanel) component.
> - Custom volume panel: a volume adjustment UI designed and displayed by the application after hiding the system volume panel, using the [AVVolumePanel](#avvolumepanel) component.

## Modules to Import

```js
import { AVVolumePanel } from '@kit.AudioKit';
```

## Properties

The [general attributes](../apis-arkui/arkui-ts/ts-component-general-attributes.md) are supported.

## AVVolumePanel

AVVolumePanel({volumeLevel?: number, volumeParameter?: AVVolumePanelParameter})

Volume panel, which can be used to display the volume adjustment panel in your application.

**Decorator**: [@Component](../../ui/state-management/arkts-create-custom-components.md#component)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Audio.Volume

| Name| Type| Mandatory| Decorator | Description                                                                                                                                                                                                   |
| -------- | -------- | -------- |--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|volumeLevel | number | No | \@Prop | Volume value set through the volume panel.<br>If this parameter is not set, the current device volume value is used.<br>This value must be between the minimum and maximum values of the current device volume.<br>If this value is greater than the maximum value of the current device volume, the maximum volume value is set.<br>If this value is less than the minimum value of the current device volume, the minimum volume value is set.<br>To obtain the maximum, minimum, and current values of the device, see [AudioVolumeGroupManager](../apis-audio-kit/arkts-apis-audio-AudioVolumeGroupManager.md). |
|volumeParameter | [AVVolumePanelParameter](#avvolumepanelparameter)  | No | \@Prop |Sets the custom parameters of the volume panel. <br>If this parameter is not set, the system volume bar is used.|

## AVVolumePanelParameter

Describes the volume panel parameters.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Audio.Volume

| Name| Type|Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- |-------- |
|position | [Position](../apis-arkui/arkui-ts/ts-types.md#position) | No | Yes | Sets the position of the volume panel. The coordinate unit is vp.<br>If this parameter is not set, the system default volume panel position is used.<br>If this parameter is set and corresponds to a valid position within the screen, the position set by the application is displayed; a position beyond the screen range is treated as an off-screen position.<br>If this parameter is set and corresponds to an off-screen position, for example, (-1, -1), the system default volume panel is hidden.<br>**Note:** If an application needs to hide the system default volume panel, it must provide a custom volume panel to ensure that users can still adjust the volume. |

## Events

The [universal events](../apis-arkui/arkui-ts/ts-component-general-events.md) are supported.

## How to Use

1. When implementing a custom volume panel, you are advised to use the volume change listening APIs of the audio framework. Based on the information returned by the callbacks, such as the volume type volumeEvent.volumeType, the volume level volumeEvent.volume, and whether to display the volume panel volumeEvent.updateUi, the application can determine whether to process the current data and display the custom volume panel. For details, see [on('streamVolumeChange')](arkts-apis-audio-AudioVolumeManager.md#onstreamvolumechange20).
2. To ensure users are aware of volume changes, applications are not allowed to adjust the volume in the background. The system will take corresponding control measures.
3. The purpose of the system volume panel is to allow users to adjust the system volume by actively operating in the application UI, rather than the application adjusting it on its own. Therefore, if an application hides the default system volume panel by setting the volume panel position parameter, it must provide a custom volume panel to ensure that users can adjust the volume normally.

## Example

To see how the volume panel works, refer to the sample code below. To experience the volume adjustment, you'll need to change the **volume** value or press the volume buttons.

```ts
import { AVVolumePanel } from '@kit.AudioKit';

@Entry
@Component
struct Index {

  @State volume: number = 0;

  build() {
    Row() {
      Column() {
        AVVolumePanel({
          volumeLevel: this.volume,
          volumeParameter: {
            position: {
              x: 100,
              y: 200
            }
          }
        })
      }
    }.width('50%').height('50%')
  }
}
```
