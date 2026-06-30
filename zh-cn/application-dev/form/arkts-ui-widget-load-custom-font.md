# ArkTS卡片使用自定义字体
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

API version 22开始新增了[ohos.graphics.text.FontCollection.getLocalInstance](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#getlocalinstance22)接口获取本地字体集实例，应用可以通过这个本地实例为卡片加载自定义字体。

## 开发步骤
1. 创建动态卡片：按照[创建ArkTS卡片](arkts-ui-widget-creation.md)里的描述创建动态卡片。

2. 在项目`entry\src\main\resources\rawfile`目录下添加自定义字体文件`xxx.ttf`。

3. 页面布局代码实现`entry/src/main/ets/widget/pages/WidgetCard.ets`。

    在卡片页面中布局两个按钮，点击按钮`load font`或按钮`unload font`，调用本地字体集实例的loadFontSync、unloadFontSync进行字体的加载、卸载。

<!-- @[loadFontSyncCard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/CustomFontWidgetCards/entry/src/main/ets/widget/pages/WidgetCard.ets) --> 

> **说明：**
>
> - 本地字体集可加载多个自定义字体，所有字体合计最大内存限制加载20MB。
>
> - 同一应用的所有卡片共用一个本地字体集实例。加载或卸载自定义字体后，所有卡片的字体显示会同步更新。


### 运行结果
![WidgetCustomFontDemo](figures/WidgetCustomFontDemo.gif)