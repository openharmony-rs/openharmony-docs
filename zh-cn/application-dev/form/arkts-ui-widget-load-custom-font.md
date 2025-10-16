# ArkTS卡片使用自定义字体
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @Brilliantry_Rui-->

ArkTS卡片开放了使用自定义字体的能力，在卡片上可以通过[ohos.graphics.text](../reference/apis-arkgraphics2d/js-apis-graphics-text.md)对象加载自定义字体，如下示例代码实现了加载自定义字体的功能。

```ts
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct loadFontSyncCard {
  private fc: text.FontCollection = text.FontCollection.getLocalInstance();
  @State content: string = "自定义字体"

  aboutToAppear(): void {
    this.fc.loadFontSync("custom", $rawfile("NotoSansCJK-Regular.ttf"))
  }
  
  aboutToDisappear(): void {
    this.fc.unloadFontSync("custom")
  }

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```