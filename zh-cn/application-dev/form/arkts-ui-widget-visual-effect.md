# ArkTS卡片玻璃特效适配
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @lucuicui-->
<!--Adviser: @HelloShuo-->

说明：支持天气卡片使用玻璃材质，提升首眼高端精致

约束：内部开放，都支持模糊提亮，仅vosa、delphi机型支持玻璃特效

## 开发步骤
1. [创建ArkTS卡片](arkts-ui-widget-creation.md)。

2、配置form_config.json

```
"metadata": [
    {
        "name": "visualEffectType",
        "value": "blurEffect,lightAnimationEffect"
    }
],
```

3、修改

### 运行结果
![WidgetCustomFontDemo](figures/WidgetCustomFontDemo.gif)