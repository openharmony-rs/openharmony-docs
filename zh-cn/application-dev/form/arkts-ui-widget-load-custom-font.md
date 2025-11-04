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
  // 在这里使用getLocalInstance访问本地字体集实例
  private fc: text.FontCollection = text.FontCollection.getLocalInstance();
  @State content: string = "默认字体"

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")  // 在此处声明组件使用自定义字体
      Button("load font")
        .onClick(() => {
          // 在此处加载自定义字体，也可以加载rawfile目录下的字体文件
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

注意：
1、同一应用的所有卡片共用一个本地字体集实例，加载、卸载自定义字体后所有卡片都会生效。

运行效果如下图所示。  
![WidgetCustomFontDemo](figures/WidgetCustomFontDemo.gif)