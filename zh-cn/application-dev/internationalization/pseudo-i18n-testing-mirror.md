# 界面镜像伪本地化测试

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## 使用场景

界面镜像测试主要检查文字阅读顺序是否出现问题。一些语言的阅读顺序不是从左到右。例如，在阿拉伯语中，界面的阅读顺序是从右到左（RTL）。

## 测试流程

1. 切换到伪本地化测试区域，如“ar-XB”。

   >  **说明：**
   >
   >  测试区域的切换接口为系统接口，需由系统应用调用。系统应用切换测试区域成功后，普通应用可以进行伪本地化测试。
   <!--RP1-->
   ```ts
   import { i18n } from '@kit.LocalizationKit';

   i18n.System.setSystemLanguage('ar-XB');
   ```
   <!--RP1End-->

2. 遍历需要测试的APP。

## 测试事项

1. 检查界面布局、文字方向和控制逻辑是否符合从右至左的阅读习惯。具体要点见[界面镜像](i18n-ui-design.md#界面镜像)章节。

2. 检查相关功能是否异常无法使用。
