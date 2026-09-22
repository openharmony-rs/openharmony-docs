# ContainerReader

**ContainerReader** is a container breakpoint component used to obtain breakpoint information based on container size in dynamic scenarios and perform responsive layout. This component returns the container's size and breakpoint in real time through [two-way binding](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters), enabling you to create and lay out components based on container size.

> **NOTE** > > - To use **ContainerReader**, the parent component of **ContainerReader** should not rely on its child components > to determine its own size. > > - Container breakpoints determine height and width breakpoint values based on the component's own actual size and > breakpoint threshold array. The component size and breakpoint information only apply to the current component and > its child components. Multiple containers on the same page can have their own independent breakpoint states. > > - The size of the **ContainerReader** component is determined by its parent container and its own layout, and is > not affected by its child components. Layout specifications under different parent containers: when the parent > container is [Flex](arkts-arkui-flex-comp.md#flex), [Column](arkts-arkui-column-comp.md#column), or > [Row](arkts-arkui-row-comp.md#row), the remaining space of **ContainerReader** is filled; when the parent > container is of other types, the parent container is filled. > > - The parameters of the **ContainerReader** API must use state variables combined with the two-way binding ( > [!! syntax](../../../ui/state-management/arkts-new-binding.md)) so that the frontend is promptly notified to > refresh the UI when the backend calculates size changes. > > - For more development guidance and complete examples on container breakpoints, see > [Container Breakpoint (ContainerReader)](../../../ui/arkts-layout-development-container-reader.md).

## Child Components

Supported

## ContainerReader

```TypeScript
ContainerReader(value: ContainerReaderInfo)
```

Creates a **ContainerReader** component and configures container reader parameters.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ContainerReaderInfo](arkts-arkui-containerreader-comp-containerreaderinfo-i.md) | Yes | Container reader configuration options, including size data and breakpoint configuration. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BreakpointOptions](arkts-arkui-containerreader-comp-breakpointoptions-i.md) | Defines the breakpoint configuration options, which are used to specify threshold parameters for container size analysis. |
| [ContainerReaderInfo](arkts-arkui-containerreader-comp-containerreaderinfo-i.md) | Defines the configuration options for the **ContainerReader** component, used to specify parameters for reading container size and obtaining breakpoint values. The component size and breakpoint values cannot be changed through this parameter. |

## Examples

### Example 1: Switching Layout Direction Based on ContainerReader Width Breakpoint

This example demonstrates how the [ContainerReader](#containerreader-1) component obtains container size and breakpoint information through two-way binding, and switches the layout direction based on the width breakpoint.

The ContainerReader component is added since API version 26.0.0.

```TypeScript
// xxx.ets
import { ContainerReader, Size } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State containerSize: Size = { width: 0, height: 0 };
  @State widthBp: WidthBreakpoint = WidthBreakpoint.WIDTH_XS;
  @State heightBp: HeightBreakpoint = HeightBreakpoint.HEIGHT_SM;
  @State columnWidth: number = 180

  build() {
    Column({space: 10}) {
      Column({space: 10}) {
        ContainerReader({
          size: this.containerSize!!, // Bind to the this.containerSize variable. When the ContainerReader size changes, this.containerSize is automatically updated.
          widthBreakpoint: this.widthBp!!,
          heightBreakpoint: this.heightBp!!
        }) {
          // Switch layout direction based on the width breakpoint
          if (this.widthBp === WidthBreakpoint.WIDTH_XS) {
            Column({space: 20}) {
              Text('Vertical layout')
              Text(`Column`)
            }
            .width('100%')
            .height('100%')
            .backgroundColor('#D5D5D5')
            .justifyContent(FlexAlign.Center)
          } else {
            Row({space: 20}) {
              Text('Horizontal layout')
              Text(`Row`)
            }
            .width('100%')
            .height('100%')
            .backgroundColor('#2787D9')
            .justifyContent(FlexAlign.Center)
          }
        }
        .backgroundColor('#F0FAFF')
      }
      .height('20%')
      .width(this.columnWidth)
      Button('Change column width')
        .onClick(()=>{
          if (this.columnWidth == 180) {
            this.columnWidth = 320;
          } else {
            this.columnWidth = 180;
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 2: Configuring Custom Breakpoints

This example demonstrates how to customize breakpoint thresholds via [breakpointConfig](arkts-arkui-containerreader-comp-attribute.md#breakpointconfig) to define various wide and narrow layout sizes, enabling more refined layout control.

The ContainerReader component and the breakpointConfig API are added since API version 26.0.0.

Tap the button to change the width of the parent container, which returns different width breakpoint values, thereby adjusting the layout direction.

```TypeScript
// xxx.ets
import { ContainerReader, Size } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State containerSize: Size = { width: 0, height: 0 };
  @State widthBp: WidthBreakpoint = WidthBreakpoint.WIDTH_XS;
  @State heightBp: HeightBreakpoint = HeightBreakpoint.HEIGHT_SM;
  @State columnWidth: number = 180

  build() {
    Column({space: 10}) {
      Column({space: 10}) {
        ContainerReader({
          size: this.containerSize!!,
          widthBreakpoint: this.widthBp!!,
          heightBreakpoint: this.heightBp!!
        }) {
          if (this.widthBp === WidthBreakpoint.WIDTH_XS || this.widthBp === WidthBreakpoint.WIDTH_SM) {
            Column({space: 10}) {
              Text('Narrow screen layout')
                .fontSize(16)
              Text(`Width breakpoint: ${this.widthBp}`)
            }
            .width('100%')
            .height('100%')
            .backgroundColor('#D5D5D5')
            .justifyContent(FlexAlign.Center)
          } else {
            Row({space: 10}) {
              Text('Wide screen layout')
                .fontSize(16)
              Text(`Width breakpoint: ${this.widthBp}`)
            }
            .width('100%')
            .height('100%')
            .backgroundColor('#2787D9')
            .justifyContent(FlexAlign.Center)
          }
        }
        .height(100)
        .width('100%')
        .backgroundColor('#F0FAFF')
        .breakpointConfig({ width: [100, 200, 400, 500], height: [0.8, 1.2] })
      }
      .height('20%')
      .width(this.columnWidth)

      Button('Change column width')
        .onClick(()=>{
          if (this.columnWidth == 180) {
            this.columnWidth = 320;
          } else {
            this.columnWidth = 180;
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 3: Dynamically Adjusting the Number of Columns Using the Width Breakpoint

This example demonstrates how to dynamically adjust the number of columns based on the width breakpoint obtained from ContainerReader, enabling adaptive layouts across multiple devices with varying column counts for different breakpoints.

The ContainerReader component is added since API version 26.0.0.

```TypeScript
// xxx.ets
import { ContainerReader, Size } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State containerSize: Size = { width: 0, height: 0 };
  @State widthBp: WidthBreakpoint = WidthBreakpoint.WIDTH_XS;
  @State columnWidth: number = 180

  build() {
    Column({space: 10}) {
      Column({space: 10}) {
        ContainerReader({
          size: this.containerSize!!,
          widthBreakpoint: this.widthBp!!
        }) {
          Row({ space: 2 }) {
            if (this.widthBp === WidthBreakpoint.WIDTH_XS || this.widthBp === WidthBreakpoint.WIDTH_SM) {
              Column() {
                Text(`Column 1`)
                  .fontColor(Color.White)
              }
              .width('100%')
              .height(60)
              .backgroundColor('#D5D5D5')
              .justifyContent(FlexAlign.Center)
              .borderRadius(8)
              .layoutWeight(1)
            } else {
              Column() {
                Text(`Column 1`)
                  .fontColor(Color.White)
              }
              .width('100%')
              .height(60)
              .backgroundColor('#D5D5D5')
              .justifyContent(FlexAlign.Center)
              .borderRadius(8)
              .layoutWeight(1)
              Column() {
                Text(`Column 2`)
                  .fontColor(Color.White)
              }
              .width('100%')
              .height(60)
              .backgroundColor('#707070')
              .justifyContent(FlexAlign.Center)
              .borderRadius(8)
              .layoutWeight(1)
            }
          }
          .width('100%')
          .height('100%')
        }
        .breakpointConfig({ width: [100, 200, 400, 500] })
        .backgroundColor('#F0FAFF')
      }
      .height('20%')
      .width(this.columnWidth)

      Button('Change column width')
        .onClick(()=>{
          if (this.columnWidth == 180) {
            this.columnWidth = 320;
          } else {
            this.columnWidth = 180;
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
