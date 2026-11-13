# SplitLayout
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ac775a54069be1728a015bce61b1790fc26fe1c8 translatedAt=2026-11-03T01:34:54.013Z pushedAt=2026-11-13T01:05:59.876Z nl=1 -->


The **SplitLayout** component provides common page layout styles, mainly used to display combined layouts of images, titles, and content containers. It is suitable for split display scenarios that require adaptation to different screen sizes (such as detail pages, settings pages, etc.). It supports adaptation to different screen widths (three layouts: ≤ 600 vp, > 600 vp and ≤ 840 vp, > 840 vp), addressing the need to display different layout styles on devices of different sizes, improving page adaptability and user experience.


> **NOTE**
>
> - This component is supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) or [universal events](ts-component-general-events.md) are set for **SplitLayout**, the compilation toolchain generates an additional node named **\_\_Common\_\_** and mounts the universal attributes or universal events on **\_\_Common\_\_** instead of applying them directly to **SplitLayout**. As a result, the universal attributes or universal events set by developers may not take effect or may not work as expected. Therefore, it is not recommended to set universal attributes and universal events for **SplitLayout**.


## Modules to Import

```
import { SplitLayout } from '@kit.ArkUI';
```

## Child Components

Not supported

## SplitLayout

SplitLayout({mainImage: ResourceStr, primaryText: ResourceStr, secondaryText?: ResourceStr, tertiaryText?: ResourceStr, container: ()&nbsp;=&gt;&nbsp;void })

Defines a split layout component that supports adaptive layout capabilities, displaying different layout styles at different widths.

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Mandatory| Decorator       | Description    |
| -------- | -------- | -------- |---------------|--------|
| mainImage | [ResourceStr](ts-types.md#resourcestr) | Yes | @State | Main image resource displayed in the upper area of the layout. Supports common image formats such as PNG, JPG, and SVG. |
| primaryText | [ResourceStr](ts-types.md#resourcestr) | Yes | @Prop | Primary title content, with no length limit. Displayed in the title area of the layout. |
| secondaryText | [ResourceStr](ts-types.md#resourcestr) | No | @Prop | Secondary title content, with no length limit. Pass this parameter when a subtitle needs to be displayed below the title. If not passed, no subtitle is displayed. |
| tertiaryText | [ResourceStr](ts-types.md#resourcestr) | No | @Prop | Auxiliary text, with no length limit. Displayed below the subtitle area. Pass this parameter when auxiliary text needs to be displayed. If not passed, no auxiliary text is displayed. |
| container | ()&nbsp;=&gt;&nbsp;void | Yes | @BuilderParam | Container component used to host custom component content in the lower area of the layout. No return value. |

## Example
This example demonstrates how to use **SplitLayout** to achieve a page layout that is both adaptable and responsive.
```ts
import { SplitLayout } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State demoImage: Resource = $r('app.media.background');

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


![Discover-fresh-hits-02](figures/Discover-fresh-hits-02.png)


Layout greater than 600 vp and less than or equal to 840 vp


![Discover-fresh-hits](figures/Discover-fresh-hits.png)


Layout greater than 840 vp


![Discover-fresh-hits-01](figures/Discover-fresh-hits-01.png)
