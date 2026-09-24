# @ohos.arkui.advanced.ArcSlider

## Modules to Import

```TypeScript
import { ArcSlider, ArcSliderPosition, ArcSliderOptions, ArcSliderOptionsConstructorOptions, ArcSliderLayoutOptions, ArcSliderLayoutOptionsConstructorOptions, ArcSliderStyleOptions, ArcSliderStyleOptionsConstructorOptions, ArcSliderValueOptions, ArcSliderValueOptionsConstructorOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ArcSliderLayoutOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptions-c.md) | Defines the layout of the arc slider. |
| [ArcSliderOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptions-c.md) | Defines the properties of the arc slider. |
| [ArcSliderStyleOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptions-c.md) | Defines the style of the arc slider. |
| [ArcSliderValueOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptions-c.md) | Defines the value of the arc slider. |

### Structs

| Name | Description |
| --- | --- |
| [ArcSlider](arkts-arkui-arkui-advanced-arcslider-arcslider-s.md) | The **ArcSlider** component is designed for circular screens on wearables to quickly adjust settings, such as the volume and brightness. |

### Interfaces

| Name | Description |
| --- | --- |
| [ArcSliderLayoutOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderlayoutoptionsconstructoroptions-i.md) | Defines the construction information for **ArcSliderLayoutValueOptions**. |
| [ArcSliderOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslideroptionsconstructoroptions-i.md) | Defines the constructor information for **ArcSliderOptions**. |
| [ArcSliderStyleOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcsliderstyleoptionsconstructoroptions-i.md) | Defines the constructor information for **ArcSliderStyleOptions**. |
| [ArcSliderValueOptionsConstructorOptions](arkts-arkui-arkui-advanced-arcslider-arcslidervalueoptionsconstructoroptions-i.md) | Defines the constructor information for **ArcSliderValueOptions**. |

### Enums

| Name | Description |
| --- | --- |
| [ArcSliderPosition](arkts-arkui-arkui-advanced-arcslider-arcsliderposition-e.md) | Defines the position of the arc slider on the screen. |

### Types

| Name | Description |
| --- | --- |
| [ArcSliderChangeHandler](arkts-arkui-arcsliderchangehandler-t.md) | Defines the callback invoked to notify the application when the progress value of the arc slider changes. |
| [ArcSliderEnlargeHandler](arkts-arkui-arcsliderenlargehandler-t.md) | Defines the callback invoked to notify the application when the arc slider is enlarged or reduced. |
| [ArcSliderTouchHandler](arkts-arkui-arcslidertouchhandler-t.md) | Defines the callback invoked to notify the application when the arc slider is touched. |

## Examples

This example demonstrates the basic usage of the ArcSlider component, supported since API version 18.

```TypeScript
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
