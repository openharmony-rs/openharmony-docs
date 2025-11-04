# ArkTS卡片使用自定义字体
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @lucuicui-->
<!--Adviser: @Brilliantry_Rui-->

ArkTS卡片开放了使用自定义字体的能力，在卡片上可以通过[ohos.graphics.text](../reference/apis-arkgraphics2d/js-apis-graphics-text.md)模块中的FontCollection对象加载自定义字体，如下示例代码实现了加载自定义字体的功能。

```ts
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct loadFontSyncCard {
  private fc: text.FontCollection = text.FontCollection.getLocalInstance();
  @State content: string = "默认字体"

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")
      Button("load font")
        .onClick(() => {
          this.fc.loadFontSync("custom", "file:///system/fonts/NotoSansCJK-Regular.ttc")
          this.content = "自定义字体"
        })
      Button("unload font")
        .onClick(() => {
          this.fc.unloadFontSync("custom")
          this.content = "默认字体"
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

运行效果如下图所示。  
![WidgetCanvasDemo](figures/WidgetCustomFontDemo.gif)