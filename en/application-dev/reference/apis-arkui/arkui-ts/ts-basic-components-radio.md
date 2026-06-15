# Radio
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

Provides radio buttons for user interaction.

>  **NOTE**
>
> - Since API version 12, the default indicator type for the **Radio** component changes from **RadioIndicatorType.DOT** to **RadioIndicatorType.TICK**.
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - By default, this component has the [margin](ts-universal-attributes-size.md#margin) spacing. The default value is **{&nbsp;top: '14px',&nbsp;right: '14px',&nbsp;bottom: '14px',&nbsp;left: '14px' }**.


## Child Components

Not supported


## APIs

Radio(options: RadioOptions)

Creates a radio button component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                 | Mandatory| Description              |
| ------- | ------------------------------------- | ---- | ------------------ |
| options | [RadioOptions](#radiooptions) | Yes  | Parameters of the radio button.|

## RadioOptions

Defines radio button information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| value | string | No| No| Value of the radio button.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| group | string | No| No| Name of the group to which the radio button belongs. Only one radio button in a given group can be selected at a time.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| indicatorType<sup>12+</sup> | [RadioIndicatorType](#radioindicatortype12) | No| Yes| Indicator type of the radio button. If no value is specified, **RadioIndicatorType.TICK** is used.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| indicatorBuilder<sup>12+</sup> | [CustomBuilder](ts-types.md#custombuilder8) | No| Yes| Custom component to indicate that the radio button is selected. This custom component is center aligned with the radio button. If this parameter is set to **undefined**, **RadioIndicatorType.TICK** is used as the indicator type.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## RadioIndicatorType<sup>12+</sup>

Sets the radio button style.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Value          | Description                          |
| --------------- | -------------------------------- | -------------------------------- |
| TICK            | 0           | Default tick icon. |
| DOT             | 1            | Default dot icon.  |
| CUSTOM          | 2         | Custom component.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### checked

checked(value: boolean)

Sets whether the radio button is selected.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether the radio button is selected.<br>Default value: **false**<br>**true**: The radio button is selected. **false**: The radio button is not selected.|

### checked<sup>18+</sup>

checked(isChecked: Optional\<boolean>)

Sets whether the radio button is selected. Compared to [checked](#checked), this API supports the **undefined** type for the **isChecked** parameter.

This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md) and [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                                        | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| isChecked | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes  | Whether the radio button is selected.<br>If **isChecked** is set to **undefined**, the default value **false** is used.<br>**true**: The radio button is selected. **false**: The radio button is not selected.|

### radioStyle<sup>10+</sup>

radioStyle(value?: RadioStyle)

Sets the style of the radio button in selected or deselected state.

Since API version 10, this API is supported in ArkTS components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                               | Mandatory| Description                              |
| ------ | ----------------------------------- | ---- | ---------------------------------- |
| value  | [RadioStyle](#radiostyle10) | No  | Style of the radio button in selected or deselected state.<br> The default values of the parameters in **RadioStyle** apply if this parameter is not set.|

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<RadioConfiguration>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | ContentModifier\<[RadioConfiguration](#radioconfiguration12)\> | Yes  | Content modifier to apply to the current component.<br>**modifier**: content modifier. You need to customize a class to implement the **ContentModifier** API.|

### contentModifier<sup>18+</sup>

contentModifier(modifier: Optional<ContentModifier\<RadioConfiguration>>)

Creates a content modifier. Compared with [contentModifier](#contentmodifier12)<sup>12+</sup>, this API supports the **undefined** type for **modifier** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| modifier | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<ContentModifier\<[RadioConfiguration](#radioconfiguration12)\>\> | Yes  | Content modifier to apply to the current component.<br>**modifier**: content modifier. You need to customize a class to implement the **ContentModifier** API.<br>If **modifier** is set to **undefined**, no content modifier is used.|

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onChange

onChange(callback: (isChecked: boolean) => void)

Triggered when the selection state of the radio button changes.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type   | Mandatory| Description                            |
| --------- | ------- | ---- | -------------------------------- |
| isChecked | boolean | Yes  | Callback invoked when the radio button selection state changes.<br>**true**: The radio button turns selected from unselected. **false**: The radio button turns unselected from selected.|

### onChange<sup>18+</sup>

onChange(callback: Optional\<OnRadioChangeCallback>)

Triggered when the selection state of the radio button changes. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[OnRadioChangeCallback](#onradiochangecallback18)> | Yes  | Callback invoked when the radio button selection state changes.<br>If **callback** is set to **undefined**, the callback will not be used.|

## OnRadioChangeCallback<sup>18+</sup>

type OnRadioChangeCallback = (isChecked: boolean) => void

Defines the callback type for radio button selection state changes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type   | Mandatory| Description                                                        |
| --------- | ------- | ---- | ------------------------------------------------------------ |
| isChecked | boolean | Yes  | Selection state of the radio button.<br>**true**: The radio button turns selected from unselected. **false**: The radio button turns unselected from selected.|

## RadioStyle<sup>10+</sup>

Defines the color of a radio button.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                  | Type                                      | Read-Only| Optional| Description                                                        |
| ---------------------- | ------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| checkedBackgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Color of the background when the radio button is selected.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_activated')**|
| uncheckedBorderColor   | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Color of the border when the radio button is deselected.<br>Default value: **$r('sys.color.ohos_id_color_switch_outline_off')**|
| indicatorColor         | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Color of the indicator when the radio button is selected. Since API version 12, this parameter takes effect only when **indicatorType** is set to **RadioIndicatorType.TICK** or **RadioIndicatorType.DOT**. When **indicatorType** is set to **RadioIndicatorType.CUSTOM**, the indicator color cannot be changed.<br>Default value: **$r('sys.color.ohos_id_color_foreground_contrary')**|

## RadioConfiguration<sup>12+</sup>

Defines a custom class to implement the **ContentModifier** API. This API inherits from [CommonConfiguration](ts-universal-attributes-content-modifier.md#commonconfigurationt).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type   | Read-Only| Optional |  Description             |
| ------ | ------ |-------------------------------- |-------------------------------- |-------------------------------- |
| value | string | No| No|Value of the radio button.|
| checked | boolean| No| No| Sets whether the radio button is selected.<br>Default value: **false**<br>**true**: The radio button is selected. **false**: The radio button is not selected.|
| triggerChange |Callback\<boolean>|No|No|Selection state changes of the radio button.<br>**true**: The radio button turns selected from unselected. **false**: The radio button turns unselected from selected.|


## Examples
### Example 1: Setting the Background Color
This example demonstrates how to set **checkedBackgroundColor** to customize the background color of a radio button.
```ts
// xxx.ets
@Entry
@Component
struct RadioExample {
  build() {
    Flex({ direction: FlexDirection.Row, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Column() {
        Text('Radio1')
        Radio({ value: 'Radio1', group: 'radioGroup' }).checked(true)
          .radioStyle({
            checkedBackgroundColor: Color.Pink
          })
          .height(50)
          .width(50)
          .onChange((isChecked: boolean) => {
            console.info('Radio1 status is ' + isChecked);
          })
      }
      Column() {
        Text('Radio2')
        Radio({ value: 'Radio2', group: 'radioGroup' }).checked(false)
          .radioStyle({
            checkedBackgroundColor: Color.Pink
          })
          .height(50)
          .width(50)
          .onChange((isChecked: boolean) => {
            console.info('Radio2 status is ' + isChecked);
          })
      }
      Column() {
        Text('Radio3')
        Radio({ value: 'Radio3', group: 'radioGroup' }).checked(false)
          .radioStyle({
            checkedBackgroundColor: Color.Pink
          })
          .height(50)
          .width(50)
          .onChange((isChecked: boolean) => {
            console.info('Radio3 status is ' + isChecked);
          })
      }
    }.padding({ top: 30 })
  }
}
```
![radio](figures/radio.gif)
### Example 2: Setting the Indicator Type
This example demonstrates how to customize the appearance of a radio button when it is selected by configuring **indicatorType** and **indicatorBuilder**.
```ts
// xxx.ets
@Entry
@Component
struct RadioExample {
  @Builder 
  indicatorBuilder() {
    // Replace $r('app.media.star') with the image resource file you use.
    Image($r("app.media.star"))
  }
  build() {
    Flex({ direction: FlexDirection.Row, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Column() {
        Text('Radio1')
        Radio({ value: 'Radio1', group: 'radioGroup',
          indicatorType:RadioIndicatorType.TICK
        }).checked(true)
          .height(50)
          .width(80)
          .onChange((isChecked: boolean) => {
            console.info('Radio1 status is ' + isChecked);
          })
      }
      Column() {
        Text('Radio2')
        Radio({ value: 'Radio2', group: 'radioGroup',
          indicatorType:RadioIndicatorType.DOT
        }).checked(false)
          .height(50)
          .width(80)
          .onChange((isChecked: boolean) => {
            console.info('Radio2 status is ' + isChecked);
          })
      }
      Column() {
        Text('Radio3')
        Radio({ value: 'Radio3', group: 'radioGroup',
          indicatorType:RadioIndicatorType.CUSTOM,
          indicatorBuilder:()=>{this.indicatorBuilder()}
        }).checked(false)
          .height(50)
          .width(80)
          .onChange((isChecked: boolean) => {
            console.info('Radio3 status is ' + isChecked);
          })
      }
    }.padding({ top: 30 })
  }
}
```
![radio](figures/radio_2.gif)
### Example 3: Implementing a Custom Radio Button
This example demonstrates how to implement a custom radio button using the **contentModifier** API.
```ts
class MyRadioStyle implements ContentModifier<RadioConfiguration> {
  type: number = 0;
  selectedColor: ResourceColor = Color.Black;

  constructor(numberType: number, colorType: ResourceColor) {
    this.type = numberType;
    this.selectedColor = colorType;
  }

  applyContent(): WrappedBuilder<[RadioConfiguration]> {
    return wrapBuilder(buildRadio);
  }
}

@Builder
function buildRadio(config: RadioConfiguration) {
  Row({ space: 30 }) {
    Circle({ width: 50, height: 50 })
      .stroke(Color.Black)
      .fill(config.checked ? (config.contentModifier as MyRadioStyle).selectedColor : Color.White)
    Button(config.checked ? "off" : "on")
      .width(100)
      .type(config.checked ? (config.contentModifier as MyRadioStyle).type : ButtonType.Normal)
      .backgroundColor('#2787D9')
      .onClick(() => {
        if (config.checked) {
          config.triggerChange(false);
        } else {
          config.triggerChange(true);
        }
      })
  }
}

@Entry
@Component
struct refreshExample {
  build() {
    Column({ space: 50 }) {
      Row() {
        Radio({ value: 'Radio1', group: 'radioGroup' })
          .contentModifier(new MyRadioStyle(1, '#004AAF'))
          .checked(false)
          .width(300)
          .height(100)
      }

      Row() {
        Radio({ value: 'Radio2', group: 'radioGroup' })
          .checked(true)
          .width(300)
          .height(60)
          .contentModifier(new MyRadioStyle(2, '#004AAF'))
      }
    }
  }
}
```
![](figures/radio_3.gif)
