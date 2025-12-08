# ArcSlider
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **ArcSlider** component is designed for circular screens on wearables to quickly adjust settings, such as the volume and brightness.

>  **NOTE**
>
>  This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import {
  ArcSlider,
  ArcSliderPosition,
  ArcSliderOptions,
  ArcSliderValueOptions,
  ArcSliderLayoutOptions,
  ArcSliderStyleOptions,
  ArcSliderValueOptionsConstructorOptions,
  ArcSliderLayoutOptionsConstructorOptions,
  ArcSliderStyleOptionsConstructorOptions,
  ArcSliderOptionsConstructorOptions
} from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## ArcSlider

ArcSlider({ options: ArcSliderOptions })

Creates an **ArcSlider** instance. The input parameter is the configuration for the arc slider.

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name   | Type                                 | Mandatory| Description                                                        |
| ------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [ArcSliderOptions](#arcslideroptions) | Yes  | Parameters of the arc slider.<br>Default value: default values of all properties of [ArcSliderOptions](#arcslideroptions)|

## ArcSliderOptions

Defines the properties of the arc slider.

**Decorator type**: @ObservedV2

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

### Properties

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| valueOptions | [ArcSliderValueOptions](#arcslidervalueoptions) | No| Yes| Value of the arc slider.<br>Default value: default values of all properties of [ArcSliderValueOptions](#arcslidervalueoptions)<br>**Decorator**: @Trace|
| layoutOptions | [ArcSliderLayoutOptions](#arcsliderlayoutoptions) | No| Yes| Layout of the arc slider.<br>Default value: default values of all properties of [ArcSliderLayoutOptions](#arcsliderlayoutoptions)<br>**Decorator**: @Trace|
| styleOptions | [ArcSliderStyleOptions](#arcsliderstyleoptions) | No| Yes| Style of the arc slider.<br>Default value: default values of all properties of [ArcSliderStyleOptions](#arcsliderstyleoptions)<br>**Decorator**: @Trace|
| digitalCrownSensitivity | [CrownSensitivity](ts-appendix-enums.md#crownsensitivity18) | No| Yes| Sensitivity to the digital crown rotation.<br>Default value: **CrownSensitivity.MEDIUM**<br>**Decorator**: @Trace|
| onTouch | [ArcSliderTouchHandler](#arcslidertouchhandler) | No| Yes| Callback invoked to notify the application when the arc slider is touched.<br>Default value: If this parameter is not provided, no callback will be invoked.<br>**Decorator**: @Trace|
| onChange | [ArcSliderChangeHandler](#arcsliderchangehandler) | No| Yes| Callback invoked to notify the application when the progress value of the arc slider changes.<br>Default value: If this parameter is not provided, no callback will be invoked.<br>**Decorator**: @Trace|
| onEnlarge | [ArcSliderEnlargeHandler](#arcsliderenlargehandler) | No| Yes| Callback invoked to notify the application when the arc slider is enlarged or reduced.<br>Default value: If this parameter is not provided, no callback will be invoked.<br>**Decorator**: @Trace|

### constructor

constructor(options?: ArcSliderOptionsConstructorOptions)

A constructor used to create an **ArcSliderOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                        |
| ------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| options | [ArcSliderOptionsConstructorOptions](#arcslideroptionsconstructoroptions) | No  | Constructor information for **ArcSliderOptions**.|

## ArcSliderValueOptions

Defines the value of the arc slider.

**Decorator type**: @ObservedV2

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

### Properties

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ---------- | ------------------------------------------------------------ |
| progress | number | No  | Yes    | Current progress.<br>Default value: same as the value of **min**.<br>**Decorator**: @Trace|
| min   | number | No  | Yes    | Minimum value.<br>Default value: **0**.<br>**Decorator**: @Trace           |
| max   | number | No  | Yes    | Maximum value.<br>Default value: **100**<br>**NOTE**<br>If the value of **min** is greater than or equal to that of **max**, **min** is set to **0** and **max** **100**.<br>If the value is not within the [min, max] range, the value of **min** or **max** is used, whichever is closer.<br>**Decorator**: @Trace|

### constructor

constructor(options?: ArcSliderValueOptionsConstructorOptions)

A constructor used to create an **ArcSliderValueOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                             |
| ------- | ------------------------------------------------------------ | ---- | --------------------------------- |
| options | [ArcSliderValueOptionsConstructorOptions](#arcslidervalueoptionsconstructoroptions) | No  | Constructor information for **ArcSliderValueOptions**.|

## ArcSliderLayoutOptions

Defines the layout of the arc slider.

**Decorator type**: @ObservedV2

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

### Properties

| Name    | Type                                   | Read-Only| Optional| Description                                                        |
| -------- | --------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| reverse  | boolean                                 | No  | Yes  | Whether the value range of the arc slider is reversed. **false**: top-to-bottom sliding.<br>**true** (default): bottom-to-top sliding.<br>**Decorator**: @Trace|
| position | [ArcSliderPosition](#arcsliderposition) | No  | Yes  | Position of the arc slider on the screen.<br>Default value: **ArcSliderPosition.RIGHT**<br>**Decorator**: @Trace|

### constructor

constructor(options?: ArcSliderLayoutOptionsConstructorOptions)

A constructor used to create an **ArcSliderLayoutOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                              |
| ------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| options | [ArcSliderLayoutOptionsConstructorOptions](#arcsliderlayoutoptionsconstructoroptions) | No  | Construction information for **ArcSliderLayoutOptions**.|

## ArcSliderStyleOptions

Defines the style of the arc slider.

**Decorator type**: @ObservedV2

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

### Properties

| Name                | Type  | Read-Only| Optional| Description                                                        |
| -------------------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| trackThickness       | number | No  | Yes  | Stroke width of the arc slider in the normal state, in vp.<br>Default value: **5**<br>Value range: [5, 16]. If the value is invalid, the default value is used.<br>**Decorator**: @Trace|
| activeTrackThickness | number | No  | Yes  | Stroke width of the arc slider when it is in an enlarged state, in vp.<br>Default value: **24**<br>Value range: [24, 36]. If the value is invalid, the default value is used.<br>**Decorator**: @Trace|
| trackColor           | string | No  | Yes  | Background color of the stroke.<br>Default value: **#33FFFFFF**<br>**Decorator**: @Trace|
| selectedColor        | string | No  | Yes  | Highlight color of the stroke.<br>Default value: **#FF5EA1FF**<br>**Decorator**: @Trace|
| trackBlur            | number | No  | Yes  | Blur effect applied to the stroke background, in vp.<br>Default value: **20**<br>If a value less than 0 is set, the default is used.<br>**Decorator**: @Trace|

### constructor

constructor(options?: ArcSliderStyleOptionsConstructorOptions)

A constructor used to create an **ArcSliderStyleOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                             |
| ------- | ------------------------------------------------------------ | ---- | --------------------------------- |
| options | [ArcSliderStyleOptionsConstructorOptions](#arcsliderstyleoptionsconstructoroptions) | No  | Constructor information for **ArcSliderStyleOptions**.|

## ArcSliderPosition

Defines the position of the arc slider on the screen.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name | Value  | Description                            |
| ----- | ---- | -------------------------------- |
| LEFT  | 0    | The arc slider is displayed on the left.|
| RIGHT | 1    | The arc slider is displayed on the right.|

## ArcSliderTouchHandler

type ArcSliderTouchHandler = (event: TouchEvent) => void

Defines the callback invoked to notify the application when the arc slider is touched.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                        | Mandatory| Description                |
| ------ | ------------------------------------------------------------ | ---- | -------------------- |
| event  | [TouchEvent](ts-universal-events-touch.md#touchevent) | Yes  | **TouchEvent** object.|

## ArcSliderChangeHandler

type ArcSliderChangeHandler = (progress: number) => void

Defines the callback invoked to notify the application when the progress value of the arc slider changes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name  | Type  | Mandatory| Description                |
| -------- | ------ | ---- | -------------------- |
| progress | number | Yes  | Current progress of the slider.|

## ArcSliderEnlargeHandler

type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void

Defines the callback invoked to notify the application when the arc slider is enlarged or reduced.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name    | Type   | Mandatory| Description                                                        |
| ---------- | ------- | ---- | ------------------------------------------------------------ |
| isEnlarged | boolean | Yes  | Whether the arc slider is enlarged.<br>**false**: The arc slider is in a reduced state.<br>**true**: The arc slider is in an enlarged state.|

## ArcSliderOptionsConstructorOptions

Defines the constructor information for **ArcSliderOptions**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name                   | Type                                                       | Read-Only| Optional| Description                                                        |
| ----------------------- | ----------------------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| valueOptions            | [ArcSliderValueOptions](#arcslidervalueoptions)             | No  | Yes  | Value of the arc slider.<br>Default value: default values of all properties of [ArcSliderValueOptions](#arcslidervalueoptions)|
| layoutOptions           | [ArcSliderLayoutOptions](#arcsliderlayoutoptions)           | No  | Yes  | Layout of the arc slider.<br>Default value: default values of all properties of [ArcSliderLayoutOptions](#arcsliderlayoutoptions)|
| styleOptions            | [ArcSliderStyleOptions](#arcsliderstyleoptions)             | No  | Yes  | Style of the arc slider.<br>Default value: default values of all properties of [ArcSliderStyleOptions](#arcsliderstyleoptions)|
| digitalCrownSensitivity | [CrownSensitivity](ts-appendix-enums.md#crownsensitivity18) | No  | Yes  | Sensitivity to the digital crown rotation.<br>Default value: **CrownSensitivity.MEDIUM**  |
| onTouch                 | [ArcSliderTouchHandler](#arcslidertouchhandler)             | No  | Yes  | Callback invoked to notify the application when the arc slider is touched.<br>Default value: If this parameter is not provided, no callback will be invoked.|
| onChange                | [ArcSliderChangeHandler](#arcsliderchangehandler)           | No  | Yes  | Callback invoked to notify the application when the progress value of the arc slider changes.<br>Default value: If this parameter is not provided, no callback will be invoked.|
| onEnlarge               | [ArcSliderEnlargeHandler](#arcsliderenlargehandler)         | No  | Yes  | Callback invoked to notify the application when the arc slider is enlarged or reduced.<br>Default value: If this parameter is not provided, no callback will be invoked.|

## ArcSliderValueOptionsConstructorOptions

Defines the constructor information for **ArcSliderValueOptions**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| progress | number | No  | Yes | Current progress.<br>Default value: same as the value of **min**.          |
| min   | number | No  | Yes | Minimum value.<br>Default value: **0**.                                 |
| max   | number | No  | Yes | Maximum value.<br>Default value: **100**<br>**NOTE**<br>If the value of **min** is greater than or equal to that of **max**, **min** is set to **0** and **max** **100**.<br>If the value is not within the [min, max] range, the value of **min** or **max** is used, whichever is closer.|

## ArcSliderLayoutOptionsConstructorOptions

Defines the construction information for **ArcSliderLayoutValueOptions**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name    | Type                                   | Read-Only| Optional| Description                                                        |
| -------- | --------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| reverse  | boolean                                 | No  | Yes  | Whether the value range of the arc slider is reversed.<br>Default value: **true** (swipe from bottom to top)|
| position | [ArcSliderPosition](#arcsliderposition) | No  | Yes  | Position of the arc slider on the screen.<br>Default value: **ArcSliderPosition.RIGHT**|

## ArcSliderStyleOptionsConstructorOptions

Defines the constructor information for **ArcSliderStyleOptions**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name                | Type  | Read-Only| Optional| Description                                                        |
| -------------------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| trackThickness       | number | No  | Yes  | Stroke width of the arc slider in the normal state, in vp.<br>Default value: **5**<br>Value range: [5, 16]. If the value is invalid, the default value is used.|
| activeTrackThickness | number | No  | Yes  | Stroke width of the arc slider when it is in an enlarged state, in vp.<br>Default value: **24**<br>Value range: [24, 36]. If the value is invalid, the default value is used.|
| trackColor           | string | No  | Yes  | Background color of the stroke.<br>Default value: **#33FFFFFF**                     |
| selectedColor        | string | No  | Yes  | Highlight color of the stroke.<br>Default value: **#FF5EA1FF**                     |
| trackBlur            | number | No  | Yes  | Blur effect applied to the stroke background, in vp.<br>Default value: **20**<br>If a value less than 0 is set, the default is used.|

## Example

This example demonstrates the basic usage of the **ArcSlider** component, supported since API version 18.

```ts
// xxx.ets
import {
  ArcSlider,
  ArcSliderPosition,
  ArcSliderOptions,
  ArcSliderValueOptions,
  ArcSliderLayoutOptions,
  ArcSliderStyleOptions,
  ArcSliderValueOptionsConstructorOptions,
  ArcSliderLayoutOptionsConstructorOptions,
  ArcSliderStyleOptionsConstructorOptions,
  ArcSliderOptionsConstructorOptions
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct ArcSliderExample {
  valueOptionsConstructorOptions: ArcSliderValueOptionsConstructorOptions = {
    progress: 60,
    min: 10,
    max: 110
  };

  layoutOptionsConstructorOptions: ArcSliderLayoutOptionsConstructorOptions = {
    reverse: true,
    position: ArcSliderPosition.RIGHT
  };
  styleOptionsConstructorOptions: ArcSliderStyleOptionsConstructorOptions = {
    trackThickness: 8,
    activeTrackThickness: 30,
    trackColor: '#ffd5d5d5',
    selectedColor: '#ff2787d9',
    trackBlur: 20
  };
  valueOptions: ArcSliderValueOptions = new ArcSliderValueOptions(this.valueOptionsConstructorOptions);
  layoutOptions: ArcSliderLayoutOptions = new ArcSliderLayoutOptions(this.layoutOptionsConstructorOptions);
  styleOptions: ArcSliderStyleOptions = new ArcSliderStyleOptions(this.styleOptionsConstructorOptions);
  arcSliderOptionsConstructorOptions: ArcSliderOptionsConstructorOptions = {
    valueOptions: this.valueOptions,
    layoutOptions: this.layoutOptions,
    styleOptions: this.styleOptions,
    digitalCrownSensitivity:CrownSensitivity.LOW,
    onTouch: (event: TouchEvent) => {
    },
    onChange: (progress: number) => {
    },
    onEnlarge: (isEnlarged: boolean) => {
    }
  };
  arcSliderOptions: ArcSliderOptions = new ArcSliderOptions(this.arcSliderOptionsConstructorOptions);

  build() {
    Column() {
      ArcSlider({ options: this.arcSliderOptions })}
      .width('100%')
  }
}
```

![arcslider](figures/arcslider.gif)
