#  ArcButton
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **ArcButton** component represents an arc button specifically designed for circular screens on wearables. It offers various button styles, such as emphasized, normal, and warning.

> **NOTE**
>
> This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import {
  ArcButton,
  ArcButtonOptions,
  ArcButtonStatus,
  ArcButtonStyleMode,
  ArcButtonPosition,
}  from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes
The [universal attributes](ts-component-general-attributes.md) are not supported.

## Events
Among the universal events, the [click event](ts-universal-events-click.md) and [touch event](ts-universal-events-touch.md) are supported.

## ArcButton

ArcButton({ options: ArcButtonOptions })

Creates an instance of **ArcButton** with configuration parameters.

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name   | Type            | Mandatory| Decorator | Description                     |
| ------- | ---------------- | ---- | ----------- | ------------------------- |
| options | [ArcButtonOptions](#arcbuttonoptions) | Yes  | @Require | Text, background color, shadow, and other parameters of the **ArcButton** component.|

## ArcButtonOptions

Defines the default or custom style parameters for the **ArcButton** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

### Properties

| Name            | Type                                                        | Read-Only| Optional| Description                                                        |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| position         | [ArcButtonPosition](#arcbuttonposition)                      | No  | No| Type of the arc button.<br>Default value: **ArcButtonPosition.BOTTOM_EDGE**|
| styleMode        | [ArcButtonStyleMode](#arcbuttonstylemode)                    | No  | No | Style mode for the arc button.<br>Default value: **ArcButtonStyleMode.EMPHASIZED_LIGHT**|
| status           | [ArcButtonStatus](#arcbuttonstatus)                          | No | No | Status of the arc button.<br>Default value: **ArcButtonStatus.NORMAL**         |
| label     | [ResourceStr](ts-types.md#resourcestr)                       | No  | No | Text displayed on the arc button.                                          |
| backgroundBlurStyle | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No  | No | Background blur style of the arc button.<br>Default value: **BlurStyle.NONE**|
| backgroundColor  | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No | No | Background color of the arc button.<br>This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.<br>Default value: **Color.Black**                |
| shadowColor      | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No | No | Shadow color of the arc button.<br>Default value: **Color.Black**                |
| shadowEnabled    | boolean                                                      | No | No | Whether to enable the shadow for the arc button.<br>Default value: **false**<br>The value **true** means to enable the shadow, and **false** means the opposite.|
| fontSize | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No | No | Font size of the arc button.<br>Default value: **19fp**                       |
| fontColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No  | No | Font color of the arc button.<br>This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.<br>Default value: **Color.White**                |
| pressedFontColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No | No | Font color of the arc button when pressed.<br>This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.<br>Default value: **Color.White**            |
| fontStyle | [FontStyle](ts-appendix-enums.md#fontstyle)                  | No | No | Font style of the arc button.<br>Default value: **FontStyle.Normal**           |
| fontFamily | string \| [Resource](ts-types.md#resource)                   | No | No | Font family of the arc button.                                            |
| fontMargin | [LocalizedMargin](ts-types.md#localizedmargin12)             | No | No | Margin of the arc button text.<br>Default value: **{ start: 24vp, top: 10vp,end: 24vp, bottom: 16vp }**|
|onTouch | [Callback](ts-types.md#voidcallback12)&lt; [TouchEvent](ts-universal-events-touch.md#touchevent)&gt; | No  | Yes | Callback triggered by touch actions on the arc button.|
|onClick | [Callback](ts-types.md#voidcallback12)&lt;[ClickEvent](ts-universal-events-click.md#clickevent) &gt; | No  | Yes | Callback triggered by click actions on the arc button.|

### constructor

constructor(options: CommonArcButtonOptions)

A constructor used to create an **ArcButton** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                             | Mandatory| Description                                         |
| ------- | ------------------------------------------------- | ---- | --------------------------------------------- |
| options | [CommonArcButtonOptions](#commonarcbuttonoptions) | Yes  | Text, background color, shadow, and other parameters of the **ArcButton** component.|

## CommonArcButtonOptions

Defines the default or custom style parameters for the **ArcButton** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name               | Type                                                        | Read-Only| Optional| Description                                                        |
| ------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| position            | [ArcButtonPosition](#arcbuttonposition)                      |No |Yes | Type of the arc button.<br>Default value: **ArcButtonPosition.BOTTOM_EDGE**|
| styleMode           | [ArcButtonStyleMode](#arcbuttonstylemode)                    | No | Yes| Style mode for the arc button.<br>Default value: **ArcButtonStyleMode.EMPHASIZED_LIGHT**|
| status              | [ArcButtonStatus](#arcbuttonstatus)                          |No  |Yes  | Status of the arc button.<br>Default value: **ArcButtonStatus.NORMAL**           |
| label               | [ResourceStr](ts-types.md#resourcestr)                       |No|Yes| Text displayed on the arc button.                                          |
| backgroundBlurStyle | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No | Yes| Background blur style of the arc button.<br>Default value: **BlurStyle.NONE**           |
| backgroundColor     | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No| Yes| Background color of the arc button.<br>This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.<br>Default value: **Color.Black**                  |
| shadowColor         | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No | Yes| Shadow color of the arc button.<br>Default value: **Color.Black**                  |
| shadowEnabled       | boolean                                                      | No| Yes| Whether to enable the shadow for the arc button.<br>Default value: **false**<br>The value **true** means to enable the shadow, and **false** means the opposite.|
| fontSize            | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No | Yes| Font size of the arc button.<br>Default value: **19fp**                         |
| fontColor           | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  |No |Yes | Font color of the arc button.<br>This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.<br>Default value: **Color.White**                  |
| pressedFontColor    | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)  | No | Yes| Font color of the arc button when pressed.<br>This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.<br>Default value: **Color.White**              |
| fontStyle           | [FontStyle](ts-appendix-enums.md#fontstyle)                  | No | Yes| Font style of the arc button.<br>Default value: **FontStyle.Normal**             |
| fontFamily          | string \| [Resource](ts-types.md#resource)                   |No |Yes | Font family of the arc button.                                            |
| fontMargin          | [LocalizedMargin](ts-types.md#localizedmargin12)             | No | Yes| Margin of the arc button text.<br>Default value: **{ start: 24vp, top: 10vp,end: 24vp, bottom: 16vp }**|
| onTouch             | [Callback](ts-types.md#voidcallback12)&lt; [TouchEvent](ts-universal-events-touch.md#touchevent)&gt; | No  | Yes | Callback triggered by touch actions on the arc button.                            |
| onClick             | [Callback](ts-types.md#voidcallback12)&lt;[ClickEvent](ts-universal-events-click.md#clickevent) &gt; | No  | Yes | Callback triggered by click actions on the arc button.                                |

## ArcButtonPosition

Enumerates the types of arc buttons that can be set for **ArcButton**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name       | Value  | Description                          |
| ----------- | ---- | -------------------------------- |
| TOP_EDGE    | 0    | Upper arc button located at the top of the circular screen.    |
| BOTTOM_EDGE | 1    | Lower arc button located at the bottom of the circular screen.|


## ArcButtonStyleMode

Enumerates the style modes that can be set for **ArcButton**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name            | Value  | Description            |
| ---------------- | ---- | ---------------- |
| EMPHASIZED_LIGHT | 0    | Emphasized, light color.|
| EMPHASIZED_DARK  | 1    | Emphasized, dark color.|
| NORMAL_LIGHT     | 2    | Normal, light color.|
| NORMAL_DARK      | 3    | Normal, dark color.|
| CUSTOM           | 4    | Custom button color and font color.|


## ArcButtonStatus

Enumerates the states that can be set for **ArcButton**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name    | Value  | Description      |
| -------- | ---- | ---------- |
| NORMAL   | 0    | Normal state.|
| PRESSED  | 1    | Pressed state.|
| DISABLED | 2    | Disabled state.|


## Example

This example shows the basic usage of the **ArcButton** component, supported since API version 18.

**topOptions** defines an upper arc button with the button text "ButtonTop," a font size of 15 fp, and shadow enabled, in the normal state with a light-color emphasized style.

**bottomOptions** defines a bottom arc button with the button text "ButtonBottom," a font size of 15 fp, shadow enabled, in a light-color emphasized style, with a click event set for the button.

To run this sample code, wearable device support is required. In the project configuration file [module.json5](../../../quick-start/module-configuration-file.md) located in the **src/main** directory, configure **wearable** under [devicetypes](../../../quick-start/module-configuration-file.md#devicetypes).

```json
// module.json5
{
  "module": {
    // ...
    "deviceTypes": [
      "wearable",
      "phone"
    ]
    // ...
  }
}
```

```ts
// xxx.ets
import {
  LengthMetrics,
  LengthUnit,
  ArcButton,
  ArcButtonOptions,
  ArcButtonStatus,
  ArcButtonStyleMode,
  ArcButtonPosition,
}  from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local topOptions: ArcButtonOptions = new ArcButtonOptions({});
  @Local bottomOptions: ArcButtonOptions = new ArcButtonOptions({});

  aboutToAppear() {
    this.topOptions = new ArcButtonOptions({
      label: 'ButtonTop',
      status: ArcButtonStatus.NORMAL,
      position: ArcButtonPosition.TOP_EDGE,
      styleMode: ArcButtonStyleMode.EMPHASIZED_LIGHT,
      fontSize: new LengthMetrics(15, LengthUnit.FP),
      shadowEnabled: true
    })

    this.bottomOptions = new ArcButtonOptions({
      label: 'ButtonBottom',
      styleMode: ArcButtonStyleMode.EMPHASIZED_LIGHT,
      fontSize: new LengthMetrics(15, LengthUnit.FP),
      shadowEnabled: true,
      onClick: () => {
        console.info('click from ArcButton.');
      }
    })
  }

  build() {
    Stack() {
      Stack() {
        Circle({ width: 233, height: 233 })
          .strokeWidth(0.1)
          .fill(Color.White)

        Column() {
          ArcButton({ options: this.topOptions })
          Blank()
          ArcButton({ options: this.bottomOptions })

        }.width('100%')
        .height('100%')
      }.width(233)
      .height(233)
    }.width('100%')
    .height('100%')
    .alignContent(Alignment.Center)
    .backgroundColor(Color.Gray)
  }
}

```

![](figures/advanced_arcButton.jpg)
