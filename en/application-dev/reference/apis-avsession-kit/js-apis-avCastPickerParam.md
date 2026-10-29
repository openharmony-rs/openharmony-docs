# @ohos.multimedia.avCastPickerParam (AVCastPicker Parameters)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester:@chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

**avCastPickerParam** provides the enumerated parameters of the [@ohos.multimedia.avCastPicker](ohos-multimedia-avcastpicker.md) components.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## AVCastPickerState

Enumerates the states of the **AVCastPicker** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| STATE_APPEARING    | 0    | The component is displayed.|
| STATE_DISAPPEARING    | 1    | The component disappears.|

## AVCastPickerStyle<sup>12+</sup>

Enumerates the styles of the **AVCastPicker** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| STYLE_PANEL    | 0    | Panel style.|
| STYLE_MENU    | 1    | Menu style.|

## AVCastPickerColorMode<sup>12+</sup>

Enumerates the color modes of the **AVCastPicker** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| AUTO    | 0    | Follows the system mode.|
| DARK    | 1    | Dark mode.|
| LIGHT    | 2    | Light mode.|
