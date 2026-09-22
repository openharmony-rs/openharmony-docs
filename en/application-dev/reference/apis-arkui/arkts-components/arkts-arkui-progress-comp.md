# Progress

The **Progress** component represents a progress indicator that displays the progress of content loading or an operation.

## Child Components

Not supported

## Progress

```TypeScript
Progress(options: ProgressOptions<Type>)
```

Creates a progress indicator.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ProgressOptions](arkts-arkui-progress-comp-progressoptions-i.md)&lt;[Type](../arkts-apis/arkts-arkui-arkui-statemanagement-type-d.md)&gt; | Yes | Options of the progress indicator, which vary by progress indicator type. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CapsuleStyleOptions](arkts-arkui-progress-comp-capsulestyleoptions-i.md) | Capsule style options. |
| [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md) | Provides common style configuration options for the progress indicator. |
| [EclipseStyleOptions](arkts-arkui-progress-comp-eclipsestyleoptions-i.md) | Options of the eclipse style. The eclipse style visualizes the progress in a way similar to the moon waxing from new to full. |
| [LinearStyleOptions](arkts-arkui-progress-comp-linearstyleoptions-i.md) | Linear style options. |
| [ProgressConfiguration](arkts-arkui-progress-comp-progressconfiguration-i.md) | Provides progress indicator configuration. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md). |
| [ProgressOptions](arkts-arkui-progress-comp-progressoptions-i.md) | Defines progress bar options. |
| [ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md) | Defines the mapping between progress indicators and styles. |
| [ProgressStyleOptions](arkts-arkui-progress-comp-progressstyleoptions-i.md) | Defines the progress bar style options. |
| [RingStyleOptions](arkts-arkui-progress-comp-ringstyleoptions-i.md) | Options of the ring style without scales. |
| [ScaleRingStyleOptions](arkts-arkui-progress-comp-scaleringstyleoptions-i.md) | Options of the ring style with scales. |
| [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md) | Defines the scan effect options. |

### Enums

| Name | Description |
| --- | --- |
| [ProgressStatus](arkts-arkui-progress-comp-progressstatus-e.md) | Current state of the progress indicator. |
| [ProgressStyle](arkts-arkui-progress-comp-progressstyle-e.md) | Enumerates progress indicator styles. |
| [ProgressType](arkts-arkui-progress-comp-progresstype-e.md) | Enumerates progress indicator types. |

## Examples

### Example 1: Setting Progress Indicator Types

This example demonstrates how to set the progress indicator type using the input parameter type of [ProgressOptions](arkts-arkui-progress-comp-progressoptions-i.md).



```TypeScript
// xxx.ets
@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Text('Linear Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 10, type: ProgressType.Linear }).width(200)
      Progress({ value: 20, total: 150, type: ProgressType.Linear }).color(Color.Grey).value(50).width(200)


      Text('Eclipse Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.Eclipse }).width(100)
        Progress({ value: 20, total: 150, type: ProgressType.Eclipse }).color(Color.Grey).value(50).width(100)
      }

      Text('ScaleRing Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.ScaleRing }).width(100)
        Progress({ value: 20, total: 150, type: ProgressType.ScaleRing })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 15, scaleCount: 15, scaleWidth: 5 })
      }

      // scaleCount vs. scaleWidth
      Row({ space: 40 }) {
        Progress({ value: 20, total: 150, type: ProgressType.ScaleRing })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 20, scaleCount: 20, scaleWidth: 5 })
        Progress({ value: 20, total: 150, type: ProgressType.ScaleRing })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 20, scaleCount: 30, scaleWidth: 3 })
      }

      Text('Ring Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.Ring }).width(100)
        Progress({ value: 20, total: 150, type: ProgressType.Ring })
          .color(Color.Grey).value(50).width(100)
          .style({ strokeWidth: 20 })
      }

      Text('Capsule Progress').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Row({ space: 40 }) {
        Progress({ value: 10, type: ProgressType.Capsule }).width(100).height(50)
        Progress({ value: 20, total: 150, type: ProgressType.Capsule })
          .color(Color.Grey)
          .value(50)
          .width(100)
          .height(50)
      }
    }.width('100%').margin({ top: 30 })
  }
}
```

### Example 2: Setting Ring Progress Indicator Attributes

This example demonstrates how to set attributes of a ring progress indicator using the strokeWidth and shadow properties in the [style](#style8) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct ProgressExample {
  private gradientColor: LinearGradient = new LinearGradient([{ color: Color.Yellow, offset: 0.5 },
    { color: Color.Orange, offset: 1.0 }]);

  build() {
    Column({ space: 15 }) {
      Text('Gradient Color').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 70, total: 100, type: ProgressType.Ring })
        .width(100).style({ strokeWidth: 20 })
        .color(this.gradientColor)

      Text('Shadow').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 70, total: 100, type: ProgressType.Ring })
        .width(120).color(Color.Orange)
        .style({ strokeWidth: 20, shadow: true })
    }.width('100%').padding({ top: 5 })
  }
}
```

### Example 3: Setting the Animation for the Ring Progress Indicator

This example demonstrates how to enable or disable animations for a ring progress indicator using the status and enableScanEffect properties in the [style](#style8) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Text('Loading Effect').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 0, total: 100, type: ProgressType.Ring })
        .width(100).color(Color.Blue)
        .style({ strokeWidth: 20, status: ProgressStatus.LOADING })

      Text('Scan Effect').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 30, total: 100, type: ProgressType.Ring })
        .width(100).color(Color.Orange)
        .style({ strokeWidth: 20, enableScanEffect: true })
    }.width('100%').padding({ top: 5 })
  }
}
```

### Example 4: Setting Capsule Progress Indicator Attributes

This example demonstrates how to set attributes for a capsule progress indicator using properties such as borderColor, borderWidth, content, font, fontColor, enableScanEffect, and showDefaultPercentage in the [style](#style8) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Row({ space: 40 }) {
        Progress({ value: 100, total: 100, type: ProgressType.Capsule }).width(100).height(50)
          .style({
            borderColor: Color.Blue,
            borderWidth: 1,
            content: 'Installing...',
            font: { size: 13, style: FontStyle.Normal },
            fontColor: Color.Gray,
            enableScanEffect: false,
            showDefaultPercentage: false
          })
      }
    }.width('100%').padding({ top: 5 })
  }
}
```

### Example 5: Setting the Smooth Effect

This example demonstrates how to enable or disable the smooth effect for the progress animation using the enableSmoothEffect property in the [style](#style8) API.



```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State value: number = 0;

  build() {
    Column({ space: 10 }) {
      Text('enableSmoothEffect: true')
        .fontSize(9)
        .fontColor(0xCCCCCC)
        .width('90%')
        .margin(5)
        .margin({ top: 20 })
      Progress({ value: this.value, total: 100, type: ProgressType.Linear })
        .style({ strokeWidth: 10, enableSmoothEffect: true })

      Text('enableSmoothEffect: false').fontSize(9).fontColor(0xCCCCCC).width('90%').margin(5)
      Progress({ value: this.value, total: 100, type: ProgressType.Linear })
        .style({ strokeWidth: 10, enableSmoothEffect: false })

      Button('value +10').onClick(() => {
        this.value += 10;
      })
        .width(75)
        .height(15)
        .fontSize(9)
    }
    .width('50%')
    .height('100%')
    .margin({ left: 20 })
  }
}
```

### Example 6: Setting the Custom Content Area

This example implements a custom progress indicator using the [contentModifier](#contentmodifier12) API. This progress indicator displays a star shape with a total progress value of 3, and the current value can be incremented or decremented through buttons. The achieved progress is filled with a custom color.



```TypeScript
// xxx.ets
class MyProgressModifier implements ContentModifier<ProgressConfiguration> {
  color: ResourceColor = Color.White;

  constructor(color: ResourceColor) {
    this.color = color;
  }

  applyContent(): WrappedBuilder<[ProgressConfiguration]> {
    return wrapBuilder(myProgress);
  }
}

@Builder
function myProgress(config: ProgressConfiguration) {

  Column({ space: 30 }) {
    Text('Current progress: ' + config.value + '/' + config.total).fontSize(20)
    Row() {
      Flex({ justifyContent: FlexAlign.SpaceBetween }) {
        Path()
          .width('30%')
          .height('30%')
          .commands('M108 0 L141 70 L218 78.3 L162 131 L175 205 L108 170 L41.2 205 L55 131 L1 78 L75 68 L108 0 Z')
          .fill(config.enabled && config.value >= 1 ? (config.contentModifier as MyProgressModifier).color :
          Color.White)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width('30%')
          .height('30%')
          .commands('M108 0 L141 70 L218 78.3 L162 131 L175 205 L108 170 L41.2 205 L55 131 L1 78 L75 68 L108 0 Z')
          .fill(config.enabled && config.value >= 2 ? (config.contentModifier as MyProgressModifier).color :
          Color.White)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width('30%')
          .height('30%')
          .commands('M108 0 L141 70 L218 78.3 L162 131 L175 205 L108 170 L41.2 205 L55 131 L1 78 L75 68 L108 0 Z')
          .fill(config.enabled && config.value >= 3 ? (config.contentModifier as MyProgressModifier).color :
          Color.White)
          .stroke(Color.Black)
          .strokeWidth(3)
      }.width('100%')
    }
  }.margin({ bottom: 100 })
}

@Entry
@Component
struct Index {
  @State currentValue: number = 0;
  modifier = new MyProgressModifier('rgb(39, 135, 217)');

  build() {
    Column() {
      Progress({ value: this.currentValue, total: 3, type: ProgressType.Ring }).contentModifier(this.modifier)
      Button('Progress++').onClick(() => {
        if (this.currentValue < 3) {
          this.currentValue += 1;
        }
      }).width('30%')
      Button('Progress--').onClick(() => {
        if (this.currentValue > 0) {
          this.currentValue -= 1;
        }
      }).width('30%').margin('10')
    }.width('100%').height('100%')
  }
}
```

### Example 7: Securing Sensitive Information

This example illustrates how to secure sensitive information using the [privacySensitive](#privacysensitive12) attribute. Note that the display requires widget framework support.



```TypeScript
@Entry
@Component
struct ProgressExample {
  build() {
    Row() {
      Column({ space: 15 }) {
        Progress({ value: 33, total: 100, type: ProgressType.Capsule }).width(300).height(50)
          .color(Color.Blue)
          .style({
            borderWidth: 5,
            font: { size: 13, style: FontStyle.Normal },
            enableScanEffect: false,
            showDefaultPercentage: true
          })
          .privacySensitive(true)
        Progress({ value: 33, total: 100, type: ProgressType.Capsule }).width(300).height(50)
          .color(Color.Blue)
          .style({
            borderWidth: 5,
            content: 'Installing...',
            font: { size: 13, style: FontStyle.Normal },
            enableScanEffect: false,
          })
          .privacySensitive(true)
      }
    }
  }
}
```

### Example 8: Setting Capsule Progress Indicator Border Radius

This example demonstrates how to set the border radius of the capsule progress indicator using the input parameter borderRadius of [CapsuleStyleOptions](arkts-arkui-progress-comp-capsulestyleoptions-i.md).

The borderRadius attribute is supported since API version 18.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ProgressExample {
  build() {
    Column({ space: 15 }) {
      Text('Capsule Progress').fontSize(9).width('90%')
      Row({ space: 15 }) {
        Progress({ value: 30, total: 100, type: ProgressType.Capsule })
          .style({ content: 'Default radius', borderWidth: 5 })
          .width(100)
          .height(60)
      }

      Row({ space: 15 }) {
        Progress({ value: 30, total: 100, type: ProgressType.Capsule })
          .style({ content: 'Radius 20 vp', borderWidth: 5, borderRadius: LengthMetrics.vp(20) })
          .width(100)
          .height(60)
      }
    }
    .width('100%')
    .margin({ top: 30 })
  }
}
```

### Example 9: Setting Attributes of Linear and Capsule Progress Indicators

This example demonstrates how to implement the gradient color of the linear progress indicator and capsule progress indicator using LinearGradient (available since API version 23) of the [color](#color) attribute.

```TypeScript
// xxx.ets
@Entry
@Component
struct ProgressExample {
  private linearGradientColor: LinearGradient = new LinearGradient([{ color: "#87BDF9", offset: 0.5 },
    { color: "#3662F0", offset: 1.0 }]);
  public capsuleGradientColor: LinearGradient = new LinearGradient([{ color: "#A5A5AF", offset: 0.5 }, 
    { color: "#67666C", offset: 1.0 }]);

  build() {
    Column({ space: 15 }) {
      Text('Linear: ').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 70, total: 100, type: ProgressType.Linear })
        .width(100).style({ strokeWidth: 20 })
        .color(this.linearGradientColor)

      Text('Capsule: ').fontSize(9).fontColor(0xCCCCCC).width('90%')
      Progress({ value: 50, total: 100, type: ProgressType.Capsule })
        .width(120).style({ strokeWidth: 40 })
        .color(this.capsuleGradientColor)
    }.width('100%').padding({ top: 5 })
  }
}
```
