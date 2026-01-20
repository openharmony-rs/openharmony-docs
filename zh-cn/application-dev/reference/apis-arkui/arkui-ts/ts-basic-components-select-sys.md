#  Select (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghaibo0-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

提供下拉选择菜单，让用户在多个选项间选择。

> **说明：**
>
> - 该组件从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本文仅介绍当前模块的系统接口，其他公开接口参见[select](./ts-basic-components-select.md)。

## menuSystemMaterial<sup>24+</sup>

menuSystemMaterial(material:Optional\<SystemUiMaterial>)

设置Select下拉菜单的系统材质。不同系统材质对应不同的属性影响效果，该接口影响背景色[backgroundColor](ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](ts-universal-attributes-border.md#borderwidth)、阴影[shadow](ts-universal-attributes-image-effect.md#shadow)，不建议与上述接口一起使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：** 

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| material | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[SystemUiMaterial](./ts-universal-attributes-image-effect-sys.md#systemuimaterial23)> | 是 | 设置下拉菜单系统材质。材质设置为非法值、undefined时，按照不设置系统材质处理。 |

## 示例
### 示例1（设置Select和下拉菜单系统材质）

该示例通过调用[menuSystemMaterial](#menusystemmaterial24)和[systemMaterial](./ts-universal-attributes-image-effect-sys.md#systemmaterial23)接口，实现select和下拉菜单系统材质效果。

从API version 24开始，新增menuSystemMaterial接口。从API version 23开始，新增systemMaterial接口。

```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Select([{ value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' },
        { value: 'SelectOption' }])
        .value('Click Show Options')
        .systemMaterial(new uiMaterail.Material({ type: uiMaterail.MaterialType.SEMI_TRANSPARENT }))
        .menuSystemMaterial(new uiMaterail.Material({ type: uiMaterail.MaterialType.SEMI_TRANSPARENT }))
    }
    // $r('app.media.img')需要替换为开发者所需的图像资源文件。
    .backgroundImage($r('app.media.img'))
  }
}
```
未设置系统材质

![select-without-menu-new-material](figures/selectWithoutNewMaterial.PNG)

设置系统材质

![select-menu-new-material](figures/selectNewMaterial.PNG)
