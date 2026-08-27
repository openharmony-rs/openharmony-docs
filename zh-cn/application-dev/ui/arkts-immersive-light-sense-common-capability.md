# 沉浸式系统材质视效
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本文介绍如何按场景定制沉浸式系统材质的视效，包括设置沉浸式系统材质反色、为沉浸式系统材质赋色、设置沉浸式系统材质交互效果以及设置沉浸式系统材质阴影效果。

## 设置沉浸式系统材质反色

当组件设置为透明度较高的沉浸式系统材质（如ULTRA_THIN或THIN）时，例如组件内的文字可能与背景色对比度不足，导致阅读体验不佳。开启[ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)中的colorInvert自动反色功能后，组件子节点中的文字颜色会自动调整为沉浸式系统材质下方背景色的反色，确保文字始终可读。具体的使用限制请参见[colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)参数说明。

如开启自动反色后文字颜色没有变化，排查步骤请参见[开启自动反色后文字颜色没有变化](arkts-immersive-light-sense-faq.md#开启自动反色后文字颜色没有变化)。

以下示例为自动反色的效果：材质下方的背景在黑白之间滚动变化，为ULTRA_THIN材质组件设置colorInvert为true后，文字颜色随背景自动反色，使文字清晰可读。

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct PageMaterialReverse {
  build() {
    Column() {
      Stack() {
        Scroll() {
          // $r('app.media.greyBackground')需要替换为开发者所需的图像资源文件
          Image($r('app.media.greyBackground'))
            .width('100%')
            .height('300%')
            .objectFit(ImageFit.Fill)
        }
        .height(400)
        .width('100%')

        Column() {
          Text('Hello World')
            .fontSize(15)
            .fontColor($r('sys.color.font_primary'))
        }
        .width(70)
        .height(50)
        .offset({ y: 20 })
        .justifyContent(FlexAlign.Center)
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          colorInvert: true,
          applyShadow: false,
        }))
        .shadow({ radius: 100, color: Color.Brown })
      }
      .height(150)
      .alignContent(Alignment.Top)
    }
    .width('100%')
    .height('100%')
  }
}
```

![colorInvert](figures/colorInvert.gif)

## 为沉浸式系统材质赋色

通过[ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)中的[materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)参数，可为材质滤镜再混合一层纯色效果，用于色调表达或降低折射的可见程度。该颜色需要带有一定的透明度，传入纯不透明颜色（如`Color.Red`或`'#FFFF0000'`）会遮挡材质滤镜效果。

> **说明：**
>
> materialColor参数对所有档位的算力设备均生效。在高算力和中算力设备上，该参数为材质滤镜再混合一层纯色效果；在低算力设备上，该参数作为背景色[backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)属性值。

以下示例为材质赋色的效果：为ULTRA_THIN材质组件设置半透明的materialColor后，材质在透出背景内容的同时呈现对应的色调。

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MaterialColorExample {
  build() {
    Stack() {
      // $r('app.media.invert')需要替换为开发者所需的图像资源文件
      Column() {}
        .width('100%')
        .height('100%')
        .backgroundImage($r('app.media.invert'))

      Column()
        .width(200)
        .height(100)
        .borderRadius(16)
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          materialColor: 'rgba(255, 255, 255, 0.4)',
        }))
    }
  }
}
```

![materialColor](figures/material-color.jpg)

## 设置沉浸式系统材质交互效果

沉浸式系统材质支持设置交互形变和点光源效果：

- **交互形变**：通过[interactive](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)开启交互形变，组件在按压时产生弹性形变，松手后自动恢复，增强交互的视觉反馈。
- **点光源**：通过[lightEffect](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)开启点光源，用户手指触摸组件时会产生流光跟随效果。lightEffect传入有效对象即启用，传入null或undefined则不启用；对象中的color字段自定义流光颜色，默认值为Color.White。

以下示例为交互形变与点光源的效果：设置interactive为true并传入lightEffect对象后，按压组件时产生弹性形变，手指触摸时产生流光跟随效果。

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct InteractiveMaterialExample {
  build() {
    Stack() {
      // $r('app.media.invert')需要替换为开发者所需的图像资源文件
      Column() {}
        .width('100%')
        .height('100%')
        .backgroundImage($r('app.media.invert'))

      Column()
        .width(200)
        .height(100)
        .borderRadius(16)
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          interactive: true,
          lightEffect: {},
        }))
    }
  }
}
```

![interactiveLight](figures/interactive-light.gif)

## 设置沉浸式系统材质阴影效果

沉浸式系统材质默认自带阴影效果（[applyShadow](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)为true），优先于[shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow)通用属性，此时自定义的shadow设置不会生效。如需使用自定义阴影，将applyShadow置为false后再设置shadow，沉浸式系统材质的阴影效果即不生效。

沉浸式系统材质自带阴影效果：

![shadowOriginal](figures/shadowOriginal.jpg)

将applyShadow置为false后设置自定义shadow（如粉色阴影）的效果，示例如下：

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct CustomShadowExample {
  build() {
    Column() {
      Stack() {
        // $r('app.media.greyBackground')需要替换为开发者所需的图像资源文件
        Image($r('app.media.greyBackground'))
          .width('100%')
          .height('300%')
          .objectFit(ImageFit.Fill)

        Column() {
          Text('Hello World')
            .fontSize(15)
            .fontColor($r('sys.color.font_primary'))
        }
        .width(70)
        .height(50)
        .offset({ y: 20 })
        .justifyContent(FlexAlign.Center)
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          applyShadow: false,
        }))
        .shadow({ radius: 100, color: Color.Brown })
      }
      .height(150)
      .alignContent(Alignment.Top)
    }
    .width('100%')
    .height('100%')
  }
}
```

![shadowPink](figures/shadowPink.jpg)
