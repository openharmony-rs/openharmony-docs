# @ohos.arkui.advanced.SplitLayout

The **SplitLayout** component provides common page layout styles, mainly used to display combined layouts of images,
 titles, and content containers. It is suitable for split display scenarios that require adaptation to different
 screen sizes (such as detail pages, settings pages, etc.). It supports adaptation to different screen widths (three
 layouts: ≤ 600 vp, > 600 vp and ≤ 840 vp, > 840 vp), addressing the need to display different layout styles on
 devices of different sizes, improving page adaptability and user experience.

> **NOTE**
 >
 > - **SplitLayout** does not support setting [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) or
 > [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md). If set, the build toolchain will generate an additional
 > \_\_Common\_\_ node and attach the universal attributes or universal events to \_\_Common\_\_ instead of directly
 > applying them to **SplitLayout** itself, causing the configured attributes or events to not take effect.

## Child Components

None

## Modules to Import

```TypeScript
import { SplitLayout } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [SplitLayout](arkts-arkui-arkui-advanced-splitlayout-splitlayout-s.md) | The **SplitLayout** component is a split layout component that supports adaptive layout and displays different layout styles at different widths. |

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
