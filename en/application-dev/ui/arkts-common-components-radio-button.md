# Radio Button (Radio)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


The **Radio** component allows users to select from a set of mutually exclusive options. Only one radio button in a given group can be selected at the same time. For details, see [Radio](../reference/apis-arkui/arkui-ts/ts-basic-components-radio.md).


## Creating a Radio Button

A radio button is created using the **Radio** component with [RadioOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-radio.md#radiooptions). The following example demonstrates how to use the **value** and **group** properties in **RadioOptions**:


```ts
Radio(options: {value: string, group: string})
```

In this API, **value** indicates the name of the radio button, and **group** indicates the name of the group to which the radio button belongs. You can use the **checked** attribute to specify whether the radio button is selected. Setting it to **true** means that the radio button is selected.

In addition, you can customize the style of the radio button for both the selected and unselected states.

```ts
Radio({ value: 'Radio1', group: 'radioGroup' })
  .checked(false)
Radio({ value: 'Radio2', group: 'radioGroup' })
  .checked(true)
```


![en-us_image_0000001562820821](figures/en-us_image_0000001562820821.png)


## Adding Events

The **Radio** component supports the [universal events](../reference/apis-arkui/arkui-ts/ts-component-general-events.md). In addition, it can be bound to the **onChange** event to execute custom logic when the selection changes.

```ts
  Radio({ value: 'Radio1', group: 'radioGroup' })
    .onChange((isChecked: boolean) => {
      if(isChecked) {
        // Operation
      }
    })
  Radio({ value: 'Radio2', group: 'radioGroup' })
    .onChange((isChecked: boolean) => {
      if(isChecked) {
        // Operation
      }
    })
```


## Example

In this example, the **Radio** components are used to switch between sound modes.


```ts
// xxx.ets
import { promptAction } from '@kit.ArkUI';

@Entry
@Component
struct RadioExample {
  @State Rst: promptAction.ShowToastOptions = { 'message': 'Ringing mode.' };
  @State Vst: promptAction.ShowToastOptions = { 'message': 'Vibration mode.' };
  @State Sst: promptAction.ShowToastOptions = { 'message': 'Silent mode.' };

  build() {
    Row() {
      Column() {
        Radio({ value: 'Radio1', group: 'radioGroup' }).checked(true)
          .height(50)
          .width(50)
          .onChange((isChecked: boolean) => {
            if (isChecked) {
              // Switch to the ringing mode.
              this.getUIContext().getPromptAction().showToast(this.Rst);
            }
          })
        Text('Ringing')
      }

      Column() {
        Radio({ value: 'Radio2', group: 'radioGroup' })
          .height(50)
          .width(50)
          .onChange((isChecked: boolean) => {
            if (isChecked) {
              // Switch to the vibration mode.
              this.getUIContext().getPromptAction().showToast(this.Vst);
            }
          })
        Text('Vibration')
      }

      Column() {
        Radio({ value: 'Radio3', group: 'radioGroup' })
          .height(50)
          .width(50)
          .onChange((isChecked: boolean) => {
            if (isChecked) {
              // Switch to the silent mode.
              this.getUIContext().getPromptAction().showToast(this.Sst);
            }
          })
        Text('Silent')
      }
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```


![en-us_image_0000001562700457](figures/en-us_image_0000001562700457.gif)
