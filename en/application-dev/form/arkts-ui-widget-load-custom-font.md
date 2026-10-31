# Using Custom Fonts in ArkTS Widgets
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=3759dbdf4c4e5bd763807e50ee88c9fec2efa9df translatedAt=2026-08-26T04:53:04.872Z pushedAt=2026-08-28T08:46:47.907Z -->

Starting from API version 22, the [ohos.graphics.text.FontCollection.getLocalInstance](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#getlocalinstance22) API has been added to obtain the local font set instance. Applications can use this local instance to load custom fonts for widgets.

## How to Develop
1. Create a widget as described in [Creating an ArkTS Widget](arkts-ui-widget-creation.md).

2. Add the custom font file `xxx.ttf` to the `entry\src\main\resources\rawfile` directory of the project.

3. Implement the page layout code in `entry/src/main/ets/widget/pages/WidgetCard.ets`.

    Add two buttons to the widget page. Tapping the `load font` button triggers **loadFontSync** to load the font, while tapping the `unload font` button triggers **unloadFontSync** to unload it.

<!-- @[loadFontSyncCard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/CustomFontWidgetCards/entry/src/main/ets/widget/pages/WidgetCard.ets) --> 

``` TypeScript
// entry/src/main/ets/widget/pages/WidgetCard.ets
import { text } from '@kit.ArkGraphics2D';

@Entry
@Component
struct LoadFontSyncCard {
  // Use getLocalInstance to access the local font set instance.
  private fc: text.FontCollection = text.FontCollection.getLocalInstance();
  @State content: string = 'Default font';

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily('custom') // Declare that the component uses the custom font here.
      Button('load font')
        .onClick(() => {
          // Load the custom font file.
          this.fc.loadFontSync('custom', $rawfile('xxx.ttf'));
          this.content = 'Custom font';
        })
      Button('unload font')
        .onClick(() => {
          this.fc.unloadFontSync('custom');
          this.content = 'Default font';
        })
    }.width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

> **NOTE**
>
> - The local font set can load multiple custom fonts, with a total memory limit of 20 MB for all loaded fonts.
>
> - All widgets in an application share a single local font set instance. After loading or unloading a custom font, the font display of all widgets is updated synchronously.


### Effect
![WidgetCustomFontDemo](figures/WidgetCustomFontDemo.gif)