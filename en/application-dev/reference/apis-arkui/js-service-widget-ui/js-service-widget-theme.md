# Theme Configuration
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->


The following theme style can be modified for a widget.

|      Name         |             Description                |
| ------------------  |  -----------------------------  |
|   app_background    |        Background color of the widget. The default color is white.       |


To modify the theme style, manually create a **resources** folder at the same level as the **pages** folder in the widget folder, and configure the theme style in the **widget/resources/styles/default.json** file. For example, the sample code below changes the default background color of a service widget to light gray.

```json
{
  "style": {
    "app_background": "#dcdcdc"
  }
}
```
