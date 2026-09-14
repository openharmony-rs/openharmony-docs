# Radio
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=0f4c8eaf8a84b06aa836773a61b889cfa832cf61 translatedAt=2026-09-03T11:50:39.714Z -->

A radio button that provides a single-selection user interaction option.

>  **NOTE**
>
> - Since API version 12, the default selected style of **Radio** changes from **RadioIndicatorType.DOT** to **RadioIndicatorType.TICK**.
>
> - This component is supported since API version 8. Newly added content in later versions is marked with a superscript to indicate the initial version of the content.
>
> - This component has a default [margin](ts-universal-attributes-size.md#margin), with the default value of {&nbsp;top: '14px',&nbsp;right: '14px',&nbsp;bottom: '14px',&nbsp;left: '14px' }.


## Child Components

Not supported


## APIs

Radio(options: RadioOptions)

Creates a radio button.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                 | Mandatory| Description              |
| ------- | ------------------------------------- | ---- | ------------------ |
| options | [RadioOptions](#radiooptions) | Yes  | Parameters of the radio button.|

## RadioOptions

Radio button information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| value | string | No| No| Current value of the radio button.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| group | string | No | No | Name of the group to which the current radio button belongs. Only one radio button in the same group can be selected. The group scope is the page where the component is located.<br/>**Widget capability:** Since API version 9, this API is supported in ArkTS cards.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| indicatorType<sup>12+</sup> | [RadioIndicatorType](#radioindicatortype12) | No | Yes | Configures the selected style of the radio button. If not set, RadioIndicatorType.TICK is used for display.<br/>**Widget capability:** Since API version 12, this API is supported in ArkTS cards.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services.<br/>**Model constraint:** This API can be used only in the stage model. |
| indicatorBuilder<sup>12+</sup> | [CustomBuilder](ts-types.md#custombuilder8) | No | Yes | Configures the selected style of the radio button as a custom component. The custom component is displayed aligned with the center of the Radio component. If indicatorBuilder is set to undefined, RadioIndicatorType.TICK is used for display.<br/>**Widget capability:** Since API version 12, this API is supported in ArkTS cards.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services.<br/>**Model constraint:** This API can be used only in the stage model. |

## RadioIndicatorType<sup>12+</sup>

Radio button style.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

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

Sets whether the radio button is selected. Compared with [checked](#checked), this API supports the **undefined** type for the **isChecked** parameter.

This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md) and [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                                        | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| isChecked | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes | Selected state of the radio button.<br/>When the value of isChecked is undefined, the default value false is used.<br/>When the value is true, the radio button is selected. When the value is false, the radio button is not selected. |

### radioStyle<sup>10+</sup>

radioStyle(value?: RadioStyle)

Sets the style of the radio button in selected or deselected state.

Since API version 10, this API is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                               | Mandatory| Description                              |
| ------ | ----------------------------------- | ---- | ---------------------------------- |
| value  | [RadioStyle](#radiostyle10) | No   | Style of the radio button in the selected and unselected states. <br/> If this parameter is not set, the default value of each parameter in RadioStyle is used. |

### contentModifier<sup>12+</sup>

contentModifier(modifier: ContentModifier\<RadioConfiguration>)

Creates a content modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------ |
| modifier  | ContentModifier\<[RadioConfiguration](#radioconfiguration12)\> | Yes   | Method for customizing the content area on the Radio component.<br/>modifier: content modifier. Developers need to customize a class to implement the ContentModifier API. |

### contentModifier<sup>18+</sup>

contentModifier(modifier: Optional<ContentModifier\<RadioConfiguration>>)

Creates a content modifier. Compared with [contentModifier](#contentmodifier12)<sup>12+</sup>, this API supports the **undefined** type for the **modifier** parameter.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| modifier | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<ContentModifier\<[RadioConfiguration](#radioconfiguration12)\>\> | Yes | Method for customizing the content area on the Radio component.<br/>modifier: content modifier. Developers need to define a custom class to implement the ContentModifier API.<br/>When the value of modifier is undefined, the content modifier is not used. |

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onChange

onChange(callback: (isChecked: boolean) => void)

Triggered when the selected state of the radio button changes.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type   | Mandatory| Description                            |
| --------- | ------- | ---- | -------------------------------- |
| isChecked | boolean | Yes  | Selected state of the radio button.<br>The value **true** means that the radio button changes from unselected to selected, and **false** means that the radio button changes from selected to unselected.|

### onChange<sup>18+</sup>

onChange(callback: Optional\<OnRadioChangeCallback>)

Triggered when the selected state of the radio button changes. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[OnRadioChangeCallback](#onradiochangecallback18)> | Yes   | Callback invoked when the selected state of the radio button changes.<br/>If the value of callback is undefined, the callback is not used. |

## OnRadioChangeCallback<sup>18+</sup>

type OnRadioChangeCallback = (isChecked: boolean) => void

Defines the callback type for radio button selected state changes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type   | Mandatory| Description                                                        |
| --------- | ------- | ---- | ------------------------------------------------------------ |
| isChecked | boolean | Yes | New selected state of the radio button after the state changes.<br/>The value `true` means that the radio button changes from unselected to selected, and `false` means that it changes from selected to unselected. |

## RadioStyle<sup>10+</sup>

Style of the radio button.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                  | Type                                      | Read-Only| Optional| Description                                                        |
| ---------------------- | ------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| checkedBackgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Color of the background when the radio button is selected.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_activated')**|
| uncheckedBorderColor   | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Color of the border when the radio button is deselected.<br>Default value: **$r('sys.color.ohos_id_color_switch_outline_off')**|
| indicatorColor         | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Color of the indicator when the radio button is selected. Since API version 12, this parameter takes effect only when **indicatorType** is set to **RadioIndicatorType.TICK** or **RadioIndicatorType.DOT**.  <br>Default value: **$r('sys.color.ohos_id_color_foreground_contrary')**|

## RadioConfiguration<sup>12+</sup>

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](ts-universal-attributes-content-modifier.md#commonconfigurationt).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type   | Read-Only| Optional |  Description             |
| ------ | ------ |-------------------------------- |-------------------------------- |-------------------------------- |
| value | string | No| No|Current value of the radio button.|
| checked | boolean| No| No| Whether the radio button is selected.<br>Default value: **false**<br>**true**: The radio button is selected. **false**: The radio button is not selected.|
| triggerChange |Callback\<boolean>| No|No|Callback used to trigger the change of the selected state of the radio button.<br/>When called with **true**, the radio button is set to the selected state; when called with **false**, it is set to the unselected state. |


## Example
### Example 1: Setting the Background Color
This example customizes the background color of the radio button by configuring checkedBackgroundColor.
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
This example customizes the selected style by configuring indicatorType and indicatorBuilder.
```ts
// xxx.ets
@Entry
@Component
struct RadioExample {
  @Builder 
  indicatorBuilder() {
    // Replace $r('app.media.star') with the image resource file you use.
    Image($r('app.media.star'))
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
This example illustrates how to implement a custom radio button using the **contentModifier** API.
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
          config.triggerChange(false); // Trigger the radio button selected state change and set it to unselected.
        } else {
          config.triggerChange(true); // Trigger the radio button selected state change and set it to selected.
        }
      })
  }
}

@Entry
@Component
struct RadioExample {
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