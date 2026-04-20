# @ohos.arkui.uiMaterial (系统材质)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供系统材质的接口定义。不同的系统材质对应不同的UI效果，包括背景色[backgroundColor](arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](arkui-ts/ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](arkui-ts/ts-universal-attributes-border.md#borderwidth)、阴影[shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow)效果、材质层滤镜效果。材质对象本身在不同算力的设备上表现存在差异，设备算力的高、中、低档由设备厂商决定，分档效果具体参考[ImmersiveMaterial](#immersivematerial)的描述。

**起始版本：** 26.0.0

## 导入模块

``` ts
import { uiMaterial } from '@kit.ArkUI';
```

## ImmersiveStyle

沉浸式材质样式枚举。不同的材质样式对应不同的材质参数，主要包括材质的模糊程度、高光效果等。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 值 | 说明              |
| ------ | --- | --------------- |
| ULTRA_THIN | 0 | 超薄样式。材质层超薄，具有很强的透明效果。 |
| THIN | 1 | 薄样式。材质层薄，具有较强的透明效果。 |
| REGULAR | 2 | 常规样式。材质层的厚度常规。 |
| THICK | 3 | 厚样式。模糊效果强。 |
| ULTRA_THICK | 4 | 超厚样式。模糊效果很强。 |

## ImmersiveOptions

沉浸式材质参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                                        | 只读 | 可选 | 说明                                                     |
| ---------- | ----------------------------------------------------------- | ---- | ------- | ----------------------------------------------------- |
| style   | [ImmersiveStyle](#immersivestyle)                                   | 否 | 是   | 材质样式。不同样式对应不同的材质参数，影响材质的厚度。<br/>**说明**：该参数仅对高档和中档算力设备的显示效果生效。<br/>默认值：ImmersiveStyle.REGULAR |
| materialColor   | [ResourceColor](arkui-ts/ts-types.md#resourcecolor)                                   | 否 | 是   | 材质层赋色，该参数会为材质滤镜再混合一层纯色效果。该颜色需要带一定的透明度值，不能为纯不透明的颜色，否则会将材质滤镜效果完全遮挡。<br/>**说明**：该参数仅对高档和中档算力设备的显示效果生效。<br/>默认值：Color.Transparent |
| colorInvert   | boolean                                   | 否 | 是   | 设置了材质对象的节点的子树是否自动适配材质到背景色的反色。<br/>若为false，则不会自动反色。<br/>若为true，则只有材质参数足够薄时才会自动反色。具体能反色的材质由系统定义，材质样式至少为THIN或ULTRA_THIN，且与设置应用的沉浸光感的强弱配置相关。材质越薄、沉浸光感越强，越容易符合反色材质的要求。<br/>自动反色能力仅对部分属性接口设置特殊资源值时生效，生效的属性接口包括：Text组件的[fontColor](arkui-ts/ts-basic-components-text.md#fontcolor)，Button组件的[fontColor](arkui-ts/ts-basic-components-button.md#fontcolor)，SymbolGlyph组件的[fontColor](arkui-ts/ts-basic-components-symbolGlyph.md#fontcolor)，Image组件的[fillColor](arkui-ts/ts-basic-components-image.md#fillcolor)，Search组件的[placeholderColor](arkui-ts/ts-basic-components-search.md#placeholdercolor)、[fontColor](arkui-ts/ts-basic-components-search.md#fontcolor10)、[searchIcon](arkui-ts/ts-basic-components-search.md#searchicon10)中的图标颜色、[cancelButton](arkui-ts/ts-basic-components-search.md#cancelbutton10)中的图标颜色、[caretStyle](arkui-ts/ts-basic-components-search.md#caretstyle10)中的光标颜色，TabContent组件的[tabBar](arkui-ts/ts-container-tabcontent.md#tabbar)属性使用[BottomTabBarStyle](arkui-ts/ts-container-tabcontent.md#bottomtabbarstyle9)样式时其中的文本和图标颜色。<br/>**说明**：该参数仅对高档和中档算力设备的显示效果生效。<br/>默认值：false |
| applyShadow   | boolean                                   | 否 | 是   | 是否添加材质的阴影效果。<br/>当该参数为true时，材质中的阴影效果固定生效，优先于[shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow)通用属性。当该参数为false时，shadow通用属性生效，材质的阴影效果不生效。<br/>**说明**：该参数仅对所有档位的算力设备的显示效果生效。<br/>默认值：true |

## Material

UI侧的系统材质对象基类。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ImmersiveMaterial

沉浸式材质类，继承自[Material](#material)。

沉浸式材质根据设备算力有分档表现，设备算力的高、中、低档由设备厂商决定，定义在系统配置文件中。在高档和中档算力设备上，影响材质层滤镜效果和阴影[shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow)效果。在低档算力设备上，影响背景色[backgroundColor](arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](arkui-ts/ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](arkui-ts/ts-universal-attributes-border.md#borderwidth)、阴影[shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow)效果。且同一材质的效果，会受到设置应用中沉浸光感配置项的影响，不同强弱程度的沉浸光感配置下，材质的参数和效果存在差异。

### constructor

constructor(options?: ImmersiveOptions)

ImmersiveMaterial的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名       | 类型                                                       | 必填 | 说明                                                         |
| ---------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
|  options      | [ImmersiveOptions](#immersiveoptions)                      | 否   | 系统材质配置选项，包括材质样式、材质层赋色等。<br/>默认值参考ImmersiveOptions接口各参数的默认值，即{style:ImmersiveStyle.REGULAR, materialColor:Color.Transparent, colorInvert:false, applyShadow:true}。    |

## 示例

### 示例1（设置沉浸式系统材质）

本示例介绍如何将沉浸式材质的[ImmersiveMaterial](#immersivematerial)对象通过[systemMaterial](arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)属性设置给组件。

从API版本26.0.0开始，新增ImmersiveMaterial对象和systemMaterial属性。

``` ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SystemMaterialPage {

  build() {
    Column() {
      Stack() {
        Image($r('app.media.bg1')) // $r('app.media.bg1')需要替换为开发者所需的图像资源文件
          .width('100%')
          .height('100%')

        Column({ space: 30 }) {
          Column() {
            Text("ULTRA_THIN")
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          }))

          Column() {
            Text("THIN")
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THIN,
          }))

          Column() {
            Text("REGULAR")
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.REGULAR,
          }))

          Column() {
            Text("THICK")
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THICK,
          }))

          Column() {
            Text("ULTRA_THICK")
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
          }))
        }
      }
      .height('90%')
      .width('90%')
    }
    .height('100%')
    .width('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```

在低档算力设备上表现：

![systemMaterial](figures/immersiveMaterialSmooth.jpg)

在中档算力设备上表现：

![systemMaterial](figures/immersiveMaterialGentle.jpg)

在高档算力设备上表现：

![systemMaterial](figures/immersiveMaterialExquisite.jpg)
