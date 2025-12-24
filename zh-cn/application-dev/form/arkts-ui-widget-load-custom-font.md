# ArkTS卡片使用自定义字体
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

API version 22开始新增了[ohos.graphics.text.FontCollection.getLocalInstance](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#getlocalinstance22)接口获取本地字体集实例，应用可以通过这个本地实例为卡片加载自定义字体。

## 开发步骤
1. [创建ArkTS卡片](arkts-ui-widget-creation.md)。

2. 在项目`entry\src\main\resources\rawfile`目录下添加自定义字体文件`xxx.ttf`。

3. 页面布局代码实现

    在卡片页面中布局两个按钮，点击按钮`load font`或按钮`unload font`，调用本地字体集实例的loadFontSync、unloadFontSync进行字体的加载、卸载。

```ts
import { text } from '@kit.ArkGraphics2D';

@Entry
@Component
struct loadFontSyncCard {
  // 在这里使用getLocalInstance访问本地字体集实例
  private fc: text.FontCollection = text.FontCollection.getLocalInstance();
  @State content: string = "默认字体";

  build() {
    Column({ space: 10 }) {
      Text(this.content)
        .fontFamily("custom")  // 在此处声明组件使用自定义字体
      Button("load font")
        .onClick(() => {
          // 在此处加载自定义字体文件
          this.fc.loadFontSync("custom", $rawfile("xxx.ttf"));
          this.content = "自定义字体";
        })
      Button("unload font")
        .onClick(() => {
          this.fc.unloadFontSync("custom");
          this.content = "默认字体";
        })
    }.width("100%")
    .height("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

> **说明：**
>
> - 本地字体集可加载多个自定义字体，内存限制最多可加载20MB的字体。
>
> - 同一应用的所有卡片共用一个本地字体集实例。加载或卸载自定义字体后，所有卡片的字体显示会同步更新。


### 运行结果
![WidgetCustomFontDemo](figures/WidgetCustomFontDemo.gif)