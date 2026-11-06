# ArcSlider

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ecf5d58a25055daa53a34747272770e0f3c1f57a translatedAt=2026-07-29T02:57:53.827Z pushedAt=2026-08-04T02:46:39.982Z -->

The **ArcSlider** component is designed for circular screens on wearables to quickly adjust settings, such as the volume and brightness.

> **NOTE**
>
> - This component is supported since API version 18. New features in later versions are marked with superscripts to indicate the initial version.
> - This component is supported on Phone, PC/2in1, Tablet, TV, and Wearable devices. In API version 22 and earlier, using it on Phone, PC/2in1, Tablet, or TV generates a compilation warning, but the component can run normally.

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

Creates an **ArcSlider** instance. The input parameter is the arc slider configuration options.

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
| onTouch | [ArcSliderTouchHandler](#arcslidertouchhandler) | No | Yes | Callback triggered when the arc slider is touched.<br/>Default value: no callback when not passed in.<br/>**Decorator:** @Trace |
| onChange | [ArcSliderChangeHandler](#arcsliderchangehandler) | No | Yes | Callback triggered when the progress value of the arc slider changes.<br/>Default value: no callback when not passed in.<br/>**Decorator:** @Trace |
| onEnlarge | [ArcSliderEnlargeHandler](#arcsliderenlargehandler) | No | Yes | Callback triggered when the arc slider is enlarged or shrunk.<br/>Default value: no callback when not passed in.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: ArcSliderOptionsConstructorOptions)

A constructor used to create an **ArcSliderOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                        |
| ------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| options | [ArcSliderOptionsConstructorOptions](#arcslideroptionsconstructoroptions) | No | Construction information of **ArcSliderOptions**. When not passed in, all sub-attributes of **ArcSliderOptions** take their default values. |

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
| max   | number | No  | Yes     | Maximum value.<br />Default value: **100**<br />**NOTE**<br/>When an abnormal situation occurs where **min** >= max, **min** takes the default value **0** and max takes the default value **100**.<br/>When progress is not within the range of [min, max], the nearest boundary value is taken: if **progress** is less than **min**, **min** is taken; if **progress** is greater than **max**, **max** is taken.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: ArcSliderValueOptionsConstructorOptions)

A constructor used to create an **ArcSliderValueOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                             |
| ------- | ------------------------------------------------------------ | ---- | --------------------------------- |
| options | [ArcSliderValueOptionsConstructorOptions](#arcslidervalueoptionsconstructoroptions) | No | Construction information of **ArcSliderValueOptions**. When not passed in, each sub-attribute of **ArcSliderValueOptions** takes its default value. |

## ArcSliderLayoutOptions

Defines the layout of the arc slider.

**Decorator type**: @ObservedV2

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

### Properties

| Name    | Type                                   | Read-Only| Optional| Description                                                        |
| -------- | --------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| reverse | boolean | No | Yes | Whether to reverse the sliding direction of the arc slider. The value **false** means sliding from top to bottom.<br />Default value: **true**, meaning sliding from bottom to top.<br/>**Decorator:** @Trace |
| position | [ArcSliderPosition](#arcsliderposition) | No  | Yes  | Position of the arc slider on the screen.<br>Default value: **ArcSliderPosition.RIGHT**<br>**Decorator**: @Trace|

### constructor

constructor(options?: ArcSliderLayoutOptionsConstructorOptions)

A constructor used to create an **ArcSliderLayoutOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                              |
| ------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| options | [ArcSliderLayoutOptionsConstructorOptions](#arcsliderlayoutoptionsconstructoroptions) | No   | Construction information of **ArcSliderLayoutOptions**. When not passed in, all sub-attributes of **ArcSliderLayoutOptions** take their default values. |

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
| trackBlur            | number | No   | Yes   | Stroke background blur value, in vp.<br />Default value: **20**<br/>Value range: [0, +∞). Abnormal values are handled as default.<br/>**Decorator:** @Trace |

### constructor

constructor(options?: ArcSliderStyleOptionsConstructorOptions)

A constructor used to create an **ArcSliderStyleOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                             |
| ------- | ------------------------------------------------------------ | ---- | --------------------------------- |
| options | [ArcSliderStyleOptionsConstructorOptions](#arcsliderstyleoptionsconstructoroptions) | No | Construction information of **ArcSliderStyleOptions**. When not passed in, all sub-attributes of **ArcSliderStyleOptions** take their default values. |

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

Triggered when the arc slider is touched.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                        | Mandatory| Description                |
| ------ | ------------------------------------------------------------ | ---- | -------------------- |
| event  | [TouchEvent](ts-universal-events-touch.md#touchevent) | Yes  | **TouchEvent** object.|

## ArcSliderChangeHandler

type ArcSliderChangeHandler = (progress: number) => void

Triggered when the progress value of the arc slider changes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name  | Type  | Mandatory| Description                |
| -------- | ------ | ---- | -------------------- |
| progress | number | Yes  | Current progress of the slider.|

## ArcSliderEnlargeHandler

type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void

Triggered when the arc slider is enlarged or shrunk.

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
| onTouch                 | [ArcSliderTouchHandler](#arcslidertouchhandler)             | No   | Yes   | Callback triggered when the arc slider is touched.<br/>Default value: no callback when not passed in. |
| onChange                | [ArcSliderChangeHandler](#arcsliderchangehandler)           | No   | Yes   | Callback triggered when the progress value of the arc slider changes.<br/>Default value: no callback when not passed in. |
| onEnlarge               | [ArcSliderEnlargeHandler](#arcsliderenlargehandler)         | No   | Yes   | Callback triggered when the arc slider is enlarged or shrunk.<br/>Default value: no callback when not passed in. |

## ArcSliderValueOptionsConstructorOptions

Defines the constructor information for **ArcSliderValueOptions**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| progress | number | No  | Yes | Current progress.<br>Default value: same as the value of **min**.          |
| min   | number | No  | Yes | Minimum value.<br>Default value: **0**.                                 |
| max   | number | No  | Yes  | Maximum value.<br />Default value: **100**<br />**NOTE**<br/>When an abnormal situation occurs where **min** >= **max**, **min** takes the default value **0** and **max** takes the default value **100**.<br/>When **progress** is not within the [min, max] range, the nearest boundary value is taken: if **progress** is less than **min**, **min** is taken; if **progress** is greater than **max**, **max** is taken. |

## ArcSliderLayoutOptionsConstructorOptions

Defines the construction information of **ArcSliderLayoutOptions**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name    | Type                                   | Read-Only| Optional| Description                                                        |
| -------- | --------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| reverse | boolean | No | Yes | Whether to reverse the sliding direction of the arc slider. The value **false** means sliding from top to bottom.<br />Default value: **true**, meaning sliding from bottom to top. |
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
| trackBlur            | number | No   | Yes   | Stroke background blur value. Unit: vp.<br />Default value: **20**<br/>Value range: [0, +∞). Abnormal values are handled as default. |

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
  // Configure the complete ArcSlider options: numeric values, layout, style, crown sensitivity, and touch/change/enlargement event callbacks.
  arcSliderOptionsConstructorOptions: ArcSliderOptionsConstructorOptions = {
    valueOptions: this.valueOptions,
    layoutOptions: this.layoutOptions,
    styleOptions: this.styleOptions,
    digitalCrownSensitivity: CrownSensitivity.LOW,
    onTouch: (event: TouchEvent) => {
      // ...
    },
    onChange: (progress: number) => {
      // ...
    },
    onEnlarge: (isEnlarged: boolean) => {
      // ...
    }
  };
  arcSliderOptions: ArcSliderOptions = new ArcSliderOptions(this.arcSliderOptionsConstructorOptions);

  build() {
    Column() {
      // Create an ArcSlider component with the configuration options.
      ArcSlider({ options: this.arcSliderOptions })
    }
    .width('100%')
  }
}
```

![arcslider](figures/arcslider.gif)