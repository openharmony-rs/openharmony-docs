# Time Picker Dialog Box (TimePickerDialog)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

A time picker dialog box is a dialog box that allows users to select a time from the 24-hour range through scrolling. This component is applicable to scenarios where users need to select a time, such as setting an alarm clock, scheduling, or booking a time. This component provides intuitive time selection interaction, supports switching between the 12-hour format and 24-hour format, and allows you to customize the style and layout, helping your app quickly implement the time selection function and improving user experience.

>  **NOTE**
>
> - The APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](../arkts-apis-uicontext-uicontext.md).
>
> - This module does not support dynamic updates for color mode (light or dark) changes. To apply a new color mode, close and reopen the dialog box.
>
> - The maximum number of rows that can be displayed varies by screen orientation: In portrait mode, the default number of rows is 5. In landscape mode, the number of rows depends on the system configuration. If no system configuration is set, the default is 3 rows. To check the specific system configuration value for landscape mode, use **$r('sys.float.ohos_id_picker_show_count_landscape')**.

## TimePickerDialog

### show<sup>(deprecated)</sup>

static show(options?: TimePickerDialogOptions)

Shows a time picker dialog box.

> **NOTE**
> 
> This API is supported since API version 8 and deprecated since API version 18. You are advised to use [showTimePickerDialog](../arkts-apis-uicontext-uicontext.md#showtimepickerdialog) instead. **showTimePickerDialog** can be called only after a [UIContext](../arkts-apis-uicontext-uicontext.md) instance is obtained.
>
> Since API version 10, you can use the [showTimePickerDialog](../arkts-apis-uicontext-uicontext.md#showtimepickerdialog) API in [UIContext](../arkts-apis-uicontext-uicontext.md), which ensures that the time picker dialog box is shown in the intended UI instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name | Type                                                       | Mandatory| Description                      |
| ------- | ----------------------------------------------------------- | ---- | -------------------------- |
| options | [TimePickerDialogOptions](#timepickerdialogoptions) | No  | Parameters of the time picker dialog box. If the parameter is not specified, the dialog box is not displayed.|

## TimePickerDialogOptions

Defines the configuration options of the time picker dialog box.

Inherited from [TimePickerOptions](ts-basic-components-timepicker.md#timepickeroptions).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| useMilitaryTime | boolean | No| Yes| Whether to display the time in 24-hour format or 12-hour format.<br>- **true**: 24-hour format.<br>- **false**: 12-hour format.<br>Default value: **false**.<br>**Note**: The enableCascade parameter takes effect only when this parameter is set to false.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| disappearTextStyle<sup>10+</sup> | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | No| Yes| Text color, font size, and font weight of edge items (the second item above or below the selected item).<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular<br>}<br>}<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only in the stage model.|
| textStyle<sup>10+</sup> | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | No| Yes| Text color, font size, and font weight of candidate items (the first item immediately above or below the selected item).<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>}<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only in the stage model.|
| selectedTextStyle<sup>10+</sup> | [PickerTextStyle](ts-picker-common.md#pickertextstyle) | No| Yes| Font color, font size, and font weight of the selected item.<br>Default value:<br>{<br>color: '#ff007dff',<br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium<br>}<br>}<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only in the stage model.|
| acceptButtonStyle<sup>12+</sup> | [PickerDialogButtonStyle](ts-picker-common.md#pickerdialogbuttonstyle12) | No| Yes| Style of the accept button.<br>Default value: See [PickerDialogButtonStyle](ts-picker-common.md#pickerdialogbuttonstyle12).<br>**NOTE**<br>1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**. If both are set to **true**, the **primary** field will remain at the default value of **false**.<br>2. The default button height is 40 vp, and the unit of **borderRadius** is vp. The default button height remains fixed even in accessibility and large-font modes. In addition, even if the button style is set to [ROUNDED_RECTANGLE](ts-basic-components-button.md#buttontype), the displayed effect is still a capsule button ([Capsule](ts-basic-components-button.md#buttontype)).<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| cancelButtonStyle<sup>12+</sup> | [PickerDialogButtonStyle](ts-picker-common.md#pickerdialogbuttonstyle12) | No| Yes| Style of the cancel button.<br>Default value: See [PickerDialogButtonStyle](ts-picker-common.md#pickerdialogbuttonstyle12).<br>**NOTE**<br>1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**. If both are set to **true**, the **primary** field will remain at the default value of **false**.<br>2. The default button height is 40 vp, and the unit of **borderRadius** is vp. The default button height remains fixed even in accessibility and large-font modes. In addition, even if the button style is set to [ROUNDED_RECTANGLE](ts-basic-components-button.md#buttontype), the displayed effect is still a capsule button ([Capsule](ts-basic-components-button.md#buttontype)).<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| alignment<sup>10+</sup>  | [DialogAlignment](ts-methods-alert-dialog-box.md#dialogalignment) | No | Yes | Alignment mode of the dialog box in the vertical direction.<br>Default value: **DialogAlignment.Default**<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only in the stage model.|
| offset<sup>10+</sup>     | [Offset](ts-types.md#offset) | No   | Yes   | Offset of the dialog box relative to the alignment position.<br>Default value: **{&nbsp;dx:&nbsp;0&nbsp;,&nbsp;dy:&nbsp;0&nbsp;}**<br>Unit: vp<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only in the stage model.|
| maskRect<sup>10+</sup>| [Rectangle](ts-methods-alert-dialog-box.md#rectangle8) | No   | Yes   | Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not.<br>Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Model restriction:** This API can be used only in the stage model.|
| onAccept | (value: [TimePickerResult](ts-basic-components-timepicker.md#timepickerresult)) => void | No| Yes| Callback invoked when the OK button in the dialog box is clicked. The callback parameter is the selected time value, which is of the **TimePickerResult** type.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| onCancel | () => void | No| Yes| Callback invoked when the cancel button in the dialog box is clicked. This callback has no parameter.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| onChange | (value: [TimePickerResult](ts-basic-components-timepicker.md#timepickerresult)) => void | No| Yes| Triggered when the text picker in the dialog box snaps to the selected item. The callback parameter is the selected time value, which is of the **TimePickerResult** type.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| backgroundColor<sup>11+</sup> | [ResourceColor](ts-types.md#resourcecolor)  | No| Yes| Backplane color of the dialog box.<br>Default value: **Color.Transparent**<br>**NOTE**<br>1. When **backgroundColor** is set to a non-transparent color, **backgroundBlurStyle** must be set to **BlurStyle.NONE**; otherwise, the color display may not meet the expected effect.<br>2. In 26.0.0 and later versions, the **backgroundColor** parameter does not take effect after **systemMaterial** is set.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| backgroundBlurStyle<sup>11+</sup> | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No| Yes| Background blur style of the dialog box.<br>Default value: **BlurStyle.COMPONENT_ULTRA_THICK**<br>**NOTE**<br>1. Setting this parameter to **BlurStyle.NONE** disables the background blur. When **backgroundBlurStyle** is set to a value other than **NONE**, do not set **backgroundColor**. If you do, the color display may not produce the expected visual effect.<br>2. Since API version 26.0.0, **backgroundBlurStyle** does not take effect after **systemMaterial** is set.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| backgroundBlurStyleOptions<sup>19+</sup> | [BackgroundBlurStyleOptions](ts-universal-attributes-background.md#backgroundblurstyleoptions10) | No| Yes| Background blur effect parameter, which is used to customize the display style of the pop-up window background blur. You can configure attributes such as the color mode, adaptive color, and zoom ratio to achieve different background blur effects.<br>**NOTE**<br>If this parameter is not set, the default effect of [backgroundBlurStyle](ts-universal-attributes-background.md#backgroundblurstyle9) (**BlurStyle.COMPONENT_ULTRA_THICK**) is used.<br>**Atomic service API**: This API can be used in atomic services since API version 19.<br>**Model restriction:** This API can be used only in the stage model.|
| backgroundEffect<sup>19+</sup> | [BackgroundEffectOptions](ts-universal-attributes-background.md#backgroundeffectoptions11) | No| Yes| Background effect parameter, which is used to customize the display effect of the pop-up window background. You can configure attributes such as the blur radius, saturation, brightness, and color to achieve different background effects.<br>**NOTE**<br>If this parameter is not set, the setting does not take effect. In this case, the background blur effect of the dialog box is determined by [backgroundBlurStyle](ts-universal-attributes-background.md#backgroundblurstyle9). If this parameter is set, the **backgroundBlurStyle** effect will be overwritten. From API version 26.0.0, after **systemMaterial** is set, neither **backgroundEffect** nor **backgroundBlurStyle** takes effect.<br>**Atomic service API**: This API can be used in atomic services since API version 19.<br>**Model restriction:** This API can be used only in the stage model.|
| onDidAppear<sup>12+</sup> | () => void | No| Yes| Event callback after the dialog box appears.<br>**NOTE**<br>1. The normal timing sequence is as follows: onWillAppear > onDidAppear > (onAccept/onCancel/onChange) > onWillDisappear > onDidDisappear.<br>2. You can set the callback event for changing the dialog box display effect in **onDidAppear**. The settings take effect next time the dialog box appears.<br>3. If the user closes the dialog box immediately after it appears, **onWillDisappear** is invoked before **onDidAppear**.<br>4. If the dialog box is closed before its entrance animation is finished, this callback is not invoked.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| onDidDisappear<sup>12+</sup> | () => void | No| Yes| Event callback after the dialog box disappears.<br>**NOTE**<br>1. The normal timing sequence is as follows: onWillAppear > onDidAppear > (onAccept/onCancel/onChange) > onWillDisappear > onDidDisappear.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| onWillAppear<sup>12+</sup> | () => void | No| Yes| Event callback when the dialog box is about to appear.<br>**NOTE**<br>1. The normal timing sequence is as follows: onWillAppear > onDidAppear > (onAccept/onCancel/onChange) > onWillDisappear > onDidDisappear.<br>2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings take effect next time the dialog box appears.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| onWillDisappear<sup>12+</sup> | () => void | No| Yes| Event callback when the dialog box is about to disappear.<br>**NOTE**<br>1. The normal timing sequence is as follows: onWillAppear > onDidAppear > (onAccept/onCancel/onChange) > onWillDisappear > onDidDisappear.<br>2. If the user closes the dialog box immediately after it appears, **onWillDisappear** is invoked before **onDidAppear**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| shadow<sup>12+</sup>              | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions)&nbsp;\|&nbsp;[ShadowStyle](ts-universal-attributes-image-effect.md#shadowstyle10)| No | Yes | Shadow of the dialog box.<br>Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise. On other devices, the dialog box has no shadow by default.<br>**NOTE**<br>In API version 26.0.0 and later, the **shadow** effect does not take effect after **systemMaterial** is set.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| dateTimeOptions<sup>12+</sup> | [DateTimeOptions](../../apis-localization-kit/js-apis-intl.md#datetimeoptionsdeprecated) | No| Yes| Whether to display leading zeros for the time. Currently, only the **hour** and **minute** parameters can be set. Setting other parameters does not take effect.<br>Default value:<br>**hour**: For the 24-hour format, the default value is **"2-digit"**, meaning the hour is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X". For the 12-hour format, the default value is **"numeric"**, meaning no leading zero.<br>**minute**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Model restriction:** This API can be used only in the stage model.|
| enableHoverMode<sup>14+</sup>     | boolean | No | Yes | Whether to enable the hover mode. The hover state refers to the interaction mode when a device such as a foldable device is in the hover and folded state, not the mouse hover state.<br>- **true**: Respond when the device is in semi-folded mode.<br>- **false**: Do not respond when the device is in semi-folded mode.<br>Default value: **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 14.<br>**Model restriction:** This API can be used only in the stage model.|
| hoverModeArea<sup>14+</sup> | [HoverModeAreaType](ts-universal-attributes-sheet-transition.md#hovermodeareatype14) | No| Yes| Display area of the dialog box in hover mode. This parameter is valid only when **enableHoverMode** is set to **true**.<br>Default value: **HoverModeAreaType.BOTTOM_SCREEN**<br>**Atomic service API**: This API can be used in atomic services since API version 14.<br>**Model restriction:** This API can be used only in the stage model.|
| onEnterSelectedArea<sup>18+</sup>   |  Callback\<[TimePickerResult](ts-basic-components-timepicker.md#timepickerresult)> | No | Yes |  Callback invoked when the sliding distance of the current column exceeds half of the height of the selected item and the item enters the selection zone during scrolling. The difference between this event and the **onChange** event is that this event is triggered in real time during the sliding, which is applicable to scenarios where a real-time listener is required. The **onChange** event is triggered after the item is moved back to the selected position, which is applicable to scenarios where the final selected value needs to be confirmed.<br>**NOTE**<br>When **enableCascade** is set to **true**, using this callback is not recommended due to the interdependent relationship between the AM/PM and hour columns. This callback indicates the moment an option enters the divider area during scrolling, and only the value of the currently scrolled column will change. The values of other non-scrolled columns will remain unchanged.<br>**Atomic service API**: This API can be used in atomic services since API version 18.<br>**Model restriction:** This API can be used only in the stage model.|
| enableCascade<sup>18+</sup>              | boolean | No | Yes | Whether the AM/PM indicator automatically switches based on the hour value. Only takes effect when **useMilitaryTime** is set to **false**.<br>- **true**: The AM/PM indicator automatically switches based on the hour value.<br>- **false**: The AM/PM indicator remains static regardless of hour changes.<br>Default value: **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.<br>**Model restriction:** This API can be used only in the stage model.|
| enableHapticFeedback<sup>18+</sup> | boolean | No | Yes | Whether to enable haptic feedback.<br>- **true**: Enable haptic feedback.<br>- **false**: Disable haptic feedback.<br>Default value: **true**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.<br>**Model restriction:** This API can be used only in the stage model.<br>**NOTE**<br>1. Whether this parameter takes effect after being set to **true** depends on hardware support.<br>2. To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module** in **src/main/module.json5** of the project.<br>"requestPermissions": [{"name": "ohos.permission.VIBRATE"}] |
| systemMaterial  | [SystemUiMaterial](ts-universal-attributes-image-effect.md#systemuimaterial) | No| Yes| System material of the dialog box.<br>**NOTE**<br>- Default value: [ImmersiveMaterial](../arkts-apis-uimaterial.md#immersivematerial) object whose **style** in [ImmersiveOptions](../arkts-apis-uimaterial.md#immersiveoptions) is **ImmersiveStyle.ULTRA_THICK** If this parameter is set to **undefined**, the default value is used.<br>- Different materials produce distinct effects. This API impacts the following attributes: [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), backgroundBlurStyle](ts-universal-attributes-background.md#backgroundblurstyle9), [backgroundEffect](ts-universal-attributes-background.md#backgroundeffect11), [borderColor](ts-universal-attributes-border.md#bordercolor), [borderWidth](ts-universal-attributes-border.md#borderwidth), and [shadow](ts-universal-attributes-image-effect.md#shadow). When the system material is set, the aforementioned attributes do not take effect.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

## Example

>  **NOTE**
>
> For clarity in UI execution context, you are advised to use the [showTimePickerDialog](../arkts-apis-uicontext-uicontext.md#showtimepickerdialog) API in [UIContext](../arkts-apis-uicontext-uicontext.md).

### Example 1: Setting the Display Time Format

This example demonstrates how to set the display time using **useMilitaryTime**, **dateTimeOptions**, and **format**.

```ts
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2020-12-25T08:30:00');

  build() {
    Column() {
      Button('TimePickerDialog 12-hour format')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            selected: this.selectTime,
            format: TimePickerFormat.HOUR_MINUTE,
            useMilitaryTime: false,
            dateTimeOptions: { hour: 'numeric', minute: '2-digit' },
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            },
            onCancel: () => {
              console.info('TimePickerDialog:onCancel()');
            },
            onChange: (value: TimePickerResult) => {
              console.info('TimePickerDialog:onChange()' + JSON.stringify(value));
            },
            onDidAppear: () => {
              console.info('TimePickerDialog:onDidAppear()');
            },
            onDidDisappear: () => {
              console.info('TimePickerDialog:onDidDisappear()');
            },
            onWillAppear: () => {
              console.info('TimePickerDialog:onWillAppear()');
            },
            onWillDisappear: () => {
              console.info('TimePickerDialog:onWillDisappear()');
            }
          });
        })
      Button('TimePickerDialog 24-hour format')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            selected: this.selectTime,
            format: TimePickerFormat.HOUR_MINUTE_SECOND,
            useMilitaryTime: true,
            onAccept: (value: TimePickerResult) => {
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            },
          })
        })
    }.width('100%')
  }
}
```

![TimePickerDialog](figures/TimePickerDialog.gif)


### Example 2: Customizing the Style

In this example, **disappearTextStyle**, **textStyle**, **selectedTextStyle**, **acceptButtonStyle**, and **cancelButtonStyle** are configured to customize the text and button style.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2020-12-25T08:30:00');

  build() {
    Column() {
      Button('TimePickerDialog 12-hour format')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            disappearTextStyle: { color: '#297bec', font: { size: 15, weight: FontWeight.Lighter } },
            textStyle: { color: Color.Black, font: { size: 20, weight: FontWeight.Normal } },
            selectedTextStyle: { color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } },
            acceptButtonStyle: {
              type: ButtonType.Normal,
              style: ButtonStyleMode.NORMAL,
              role: ButtonRole.NORMAL,
              fontColor: 'rgb(81, 81, 216)',
              fontSize: '26fp',
              fontWeight: FontWeight.Bolder,
              fontStyle: FontStyle.Normal,
              fontFamily: 'sans-serif',
              backgroundColor: '#A6ACAF',
              borderRadius: 20
            },
            cancelButtonStyle: {
              type: ButtonType.Normal,
              style: ButtonStyleMode.NORMAL,
              role: ButtonRole.NORMAL,
              fontColor: Color.Blue,
              fontSize: '16fp',
              fontWeight: FontWeight.Normal,
              fontStyle: FontStyle.Italic,
              fontFamily: 'sans-serif',
              backgroundColor: '#50182431',
              borderRadius: 10
            },
            onAccept: (value: TimePickerResult) => {
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```

![TimePickerDialog](figures/TimePickerDialog_CustomButton.png)

### Example 3: Configuring a Dialog Box in the Hover State

This example demonstrates how to set the layout area of a dialog box in hover mode on a foldable device.

```ts
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2020-12-25T08:30:00');

  build() {
    Column() {
      Button('TimePickerDialog 12-hour format')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            selected: this.selectTime,
            disappearTextStyle: { color: Color.Red, font: { size: 15, weight: FontWeight.Lighter } },
            textStyle: { color: Color.Black, font: { size: 20, weight: FontWeight.Normal } },
            selectedTextStyle: { color: Color.Blue, font: { size: 30, weight: FontWeight.Bolder } },
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            },
            onCancel: () => {
              console.info('TimePickerDialog:onCancel()');
            },
            onChange: (value: TimePickerResult) => {
              console.info('TimePickerDialog:onChange()' + JSON.stringify(value));
            },
            onDidAppear: () => {
              console.info('TimePickerDialog:onDidAppear()');
            },
            onDidDisappear: () => {
              console.info('TimePickerDialog:onDidDisappear()');
            },
            onWillAppear: () => {
              console.info('TimePickerDialog:onWillAppear()');
            },
            onWillDisappear: () => {
              console.info('TimePickerDialog:onWillDisappear()');
            },
            enableHoverMode: true,
            hoverModeArea: HoverModeAreaType.TOP_SCREEN
          });
        })
    }.width('100%')
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 4: Setting the Dialog Box Position

This example demonstrates how to set the position of a dialog box using **alignment** and **offset**.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2020-12-25T08:30:00');

  build() {
    Column() {
      Button('TimePickerDialog')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            alignment: DialogAlignment.Center,
            offset: { dx: 20 , dy: 0 },
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```

![TimePickerDialog](figures/TimePickerDialogDemo4.png)

### Example 5: Setting the Mask Area

This example demonstrates how to set the mask area using **maskRect**.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2020-12-25T08:30:00');

  build() {
    Column() {
      Button('TimePickerDialog')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            maskRect: { x: 30, y: 60, width: '100%', height: '60%' },
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```

![TimePickerDialog](figures/TimePickerDialogDemo5.png)

### Example 6: Setting the Background

This example describes how to customize the background effect by setting [backgroundColor](#timepickerdialogoptions) and [shadow](#timepickerdialogoptions).

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2020-12-25T08:30:00');

  build() {
    Column() {
      Button('TimePickerDialog')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            backgroundColor: 'rgb(204, 226, 251)',
            backgroundBlurStyle: BlurStyle.NONE,
            shadow: ShadowStyle.OUTER_FLOATING_SM,
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```
![TimePickerDialog](figures/TimePickerDialogDemo6.png)

### Example 7: Setting the Start Time

This example demonstrates how to set the start time for the time picker dialog box.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2022-07-22T08:50:00');

  build() {
    Column() {
      Button('TimePickerDialog')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            useMilitaryTime: false,
            selected: this.selectTime,
            format: TimePickerFormat.HOUR_MINUTE_SECOND,
            start: new Date('2022-07-22T08:30:00'),
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```
![TimePickerDialog](figures/TimePickerDialogDemo7.png)

### Example 8: Setting the End Time

This example demonstrates how to set the end time for the time picker dialog box.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2022-07-22T08:50:00');

  build() {
    Column() {
      Button('TimePickerDialog')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            useMilitaryTime: false,
            selected: this.selectTime,
            format: TimePickerFormat.HOUR_MINUTE_SECOND,
            end: new Date('2022-07-22T15:20:00'),
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```
![TimePickerDialog](figures/TimePickerDialogDemo8.png)

### Example 9: Enabling the AM/PM Indicator to Automatically Switch Based on the Hour Value in 12-hour Format

This example demonstrates how to enable the AM/PM indicator to automatically switch based on the hour value in 12-hour format using **enableCascade**.

```ts
// xxx.ets
@Entry
@Component
struct TimePickerDialogExample {
  private selectTime: Date = new Date('2022-07-22T08:00:00');

  build() {
    Column() {
      Button('TimePickerDialog')
        .margin(20)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            useMilitaryTime: false,
            selected: this.selectTime,
            enableCascade: true,
            onAccept: (value: TimePickerResult) => {
              // Set selectTime to the time when the OK button is clicked. In this way, when the dialog box is displayed again, the selected time is the time when the operation was confirmed last time.
              if (value.hour != undefined && value.minute != undefined) {
                this.selectTime.setHours(value.hour, value.minute);
                console.info('TimePickerDialog:onAccept()' + JSON.stringify(value));
              }
            }
          });
        })
    }.width('100%')
  }
}
```

![TimePicker](figures/TimePickerDialogDemo9.gif)

### Example 10: Customizing the Background Blur Effect

This example demonstrates how to customize the background blur effect by configuring [backgroundBlurStyleOptions](#timepickerdialogoptions). This functionality is supported since API version 19.

```ts
@Entry
@Component
struct TimePickerDialogExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      // Replace $r('app.media.bg') with the image resource file you use.
      Image($r('app.media.bg'))
      Column() {
        Button('TimePickerDialog')
          .margin(20)
          .onClick(() => {
            this.getUIContext().showTimePickerDialog({
              backgroundColor: undefined,
              backgroundBlurStyle: BlurStyle.Thin,
              backgroundBlurStyleOptions: {
                colorMode: ThemeColorMode.LIGHT,
                adaptiveColor: AdaptiveColor.AVERAGE,
                scale: 1,
                blurOptions: { grayscale: [20, 20] },
              },
            });
          })
      }.width('100%')
    }
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 11: Customizing the Background Effect

This example demonstrates how to customize the background effect by configuring [backgroundEffect](#timepickerdialogoptions). This functionality is supported since API version 19.

```ts
@Entry
@Component
struct TimePickerDialogExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      // Replace $r('app.media.bg') with the image resource file you use.
      Image($r('app.media.bg'))
      Column() {
        Button('TimePickerDialog')
          .margin(20)
          .onClick(() => {
            this.getUIContext().showTimePickerDialog({
              backgroundColor: undefined,
              backgroundBlurStyle: BlurStyle.Thin,
              backgroundEffect: {
                radius: 60,
                saturation: 0,
                brightness: 1,
                color: Color.White,
                blurOptions: { grayscale: [20, 20] }
              },
            });
          })
      }.width('100%')
    }
  }
}
```

<!--Del--> <!--DelEnd-->


### Example 12: Setting the System Material

In this example, the system material effect is implemented by configuring [systemMaterial](#timepickerdialogoptions).

The **systemMaterial** attribute is added to **TimePickerDialogOptions** since API version 26.0.0.

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct DatePickerDialogExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      Column() {
        Button('TimePickerDialog')
          .margin(20)
          .onClick(() => {
            this.getUIContext().showTimePickerDialog({
              systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.ULTRA_THICK })
            });
          })
      }.width('100%')
    }
  }
}
```

<!--Del--> <!--DelEnd-->
