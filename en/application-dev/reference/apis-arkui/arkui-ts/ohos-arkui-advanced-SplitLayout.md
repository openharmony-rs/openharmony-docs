# SplitLayout
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fengluochenai-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->


**SplitLayout** is a component that enables you to divide the available space vertically into separate sections, each of which can contain solely text or a combination of text and images.


> **NOTE**
>
> - This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - If the **SplitLayout** component has [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **SplitLayout** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **SplitLayout** component.


## Modules to Import

```
import { SplitLayout } from '@kit.ArkUI';
```


## Child Components

Not supported

## SplitLayout

SplitLayout({mainImage: Resource, primaryText: string, secondaryText?: string, tertiaryText?: string, container: () =&gt; void })

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Mandatory| Decorator       | Description    |
| -------- | -------- | -------- |---------------|--------|
| mainImage | [ResourceStr](ts-types.md#resourcestr) | Yes| @State | Image. |
| primaryText | [ResourceStr](ts-types.md#resourcestr) | Yes| @Prop         | Title. |
| secondaryText | [ResourceStr](ts-types.md#resourcestr) | No| @Prop         | Subtitle.|
| tertiaryText | [ResourceStr](ts-types.md#resourcestr) | No| @Prop         | Auxiliary text. |
| container | () =&gt; void | Yes| @BuilderParam | Container in the component.|

## Events
The [universal events](ts-component-general-events.md) are not supported.

## Example
This example demonstrates how to use **SplitLayout** to achieve a page layout that is both adaptable and responsive.
```ts
import { SplitLayout } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State demoImage: Resource = $r("app.media.background");

  build() {
    Column() {
      SplitLayout({
        mainImage: this.demoImage,
        primaryText:'New music recommendation',
        secondaryText: 'Get a playlist tailored to your taste;',
        tertiaryText: 'Updated every day',
      }) {
        Text('Example: Components can be added to a blank area container.')
          .margin({ top: 36 })
      }
    }
    .justifyContent(FlexAlign.SpaceBetween)
    .height('100%')
    .width('100%')
  }
}
```


Layout less than or equal to 600 vp


![en-us_image_0000001665553957](figures/en-us_image_0000001665553957.png)


Layout greater than 600 vp and less than or equal to 840 vp


![en-us_image_0000001616957408](figures/en-us_image_0000001616957408.png)


Layout greater than 840 vp


![en-us_image_0000001617116972](figures/en-us_image_0000001617116972.png)
