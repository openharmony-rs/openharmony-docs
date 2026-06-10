# Theme Configuration
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7b6b884ef565767a6c9d0d7139fb4cb24a435447 translatedAt=2026-06-05T10:29:36.784Z pushedAt=2026-06-08T06:55:03.781Z -->


To configure the theme for a service widget, use the attribute described below.

|      Name         |             Description                |
| ------------------  |  -----------------------------  |
|   app_background    |        Background color of the widget.       |


To configure the theme, create the **resources** folder at the same level as **pages** in the **widget** folder and set the above attribute in the **widget/resources/styles/default.json** file. For example, to configure the default theme of a widget to light gray:

```json
{
  "style": {
    "app_background": "#dcdcdc"
  }
}
```