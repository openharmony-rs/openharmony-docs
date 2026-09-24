# @ohos.arkui.advanced.SplitLayout

## Modules to Import

```TypeScript
import { SplitLayout } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [SplitLayout](arkts-arkui-arkui-advanced-splitlayout-splitlayout-s.md) | The **SplitLayout** component provides common page layout styles, mainly used to display combined layouts of images, titles, and content containers. It is suitable for split display scenarios that require adaptation to different screen sizes (such as detail pages, settings pages, etc.). It supports adaptation to different screen widths (three layouts: ≤ 600 vp, &gt; 600 vp and ≤ 840 vp, &gt; 840 vp), addressing the need to display different layout styles on devices of different sizes, improving page adaptability and user experience. |

## Examples

This example demonstrates how to use SplitLayout to achieve a page layout that is both adaptable and responsive.

```TypeScript
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
