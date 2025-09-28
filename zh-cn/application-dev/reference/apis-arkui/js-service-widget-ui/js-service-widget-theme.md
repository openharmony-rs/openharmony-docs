# 设置主题样式
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->


卡片目前支持修改的主题样式如下：

|      名称          |             描述                 |
| ------------------  |  -----------------------------  |
|   app_background    |        设置卡片背景颜色。默认为纯白色。        |


修改主题样式需要在widget文件夹下手动创建与pages同级的resources文件夹，在widget/resources/styles/default.json文件中配置主题样式。例如，修改卡片默认的背景色为浅灰色：

```json
{
  "style": {
    "app_background": "#dcdcdc"
  }
}
```