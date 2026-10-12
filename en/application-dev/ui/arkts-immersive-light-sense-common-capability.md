# Immersive System Material Visual Effects
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=96058fa5ed998d30421d812a34634716f19e7d96 translatedAt=2026-10-12T09:15:51.811Z pushedAt=2026-10-12T11:10:05.369Z -->

This topic describes how to customize the visual effects of the immersive system material by scenario, including setting immersive system material color inversion, applying color tinting to the immersive system material, setting immersive system material interactive effects, and setting immersive system material shadow effects.

## Setting Color Inversion for Immersive System Material

When a component is set to an immersive system material with high transparency (such as ULTRA_THIN or THIN), the text inside the component may lack sufficient contrast against the background color, resulting in a poor reading experience. After you enable the automatic color inversion feature through `colorInvert` in [ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions), the text color in the component's child nodes is automatically adjusted to the inverse of the background color beneath the immersive system material, ensuring that the text remains readable. For details about the usage restrictions, see the description of the [colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter.

If the text color does not change after you enable automatic color inversion, see [Text Color Does Not Change After Enabling Automatic Color Inversion](arkts-immersive-light-sense-faq.md#text-color-does-not-change-after-enabling-automatic-color-inversion) for troubleshooting steps.

The following example demonstrates the effect of automatic color inversion in the balanced mode of a high computing power device: the background beneath the material alternates  between black and white. After the **ULTRA_THIN** material with **colorInvert** set to **true** is applied to the **TabBar** component, the text and icon colors inside the **TabBar** automatically invert according to the background, keeping the text and icons clearly readable.

<!-- @[material_color_invert](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsImmersiveLightSense/entry/src/main/ets/pages/MaterialColorInvertExample.ets) -->

``` TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Component
struct ContentOne {
  build() {
    Scroll() {
      Column() {
        // Replace $r('app.media.greyBackground') with the image resource file you need.
        Image($r('app.media.greyBackground'))
          .width('100%')
          .height('150%')
          .objectFit(ImageFit.Fill)
        // Replace $r('app.media.greyBackground') with the image resource file you need.
        Image($r('app.media.greyBackground'))
          .width('100%')
          .height('150%')
          .objectFit(ImageFit.Fill)
      }
      .width('100%')
    }
    .width('100%')
    .height('100%')
  }
}

@Entry
@Component
struct PageMaterialReverse {
  build() {
    Column() {
      Tabs({ barPosition: BarPosition.End }) {
        TabContent() {
          ContentOne()
        }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'tab1')
        // The BottomTabBarStyle style supports color inversion. Set a system color resource that supports color inversion.
          .labelStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
          .iconStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
        )

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'tab2')
          .labelStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
          .iconStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
        )
      }
      .barFloatingStyle({
        adaptToHandedness: true,
        systemMaterial: new uiMaterial.ImmersiveMaterial(
          {
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            // Set the tabBar material to allow color inversion. Color inversion takes effect only when the style is ULTRA_THIN or THIN.
            colorInvert: true,
          }
        )
      })
      .barOverlap(true)
      .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```


![colorInvert](figures/colorInvert.gif)

## Color Tinting for Immersive System Material

Through the [materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter in [ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions), you can blend an additional solid color into the material filter to express a color tone or reduce the visibility of refraction. This color must have a certain degree of transparency. Passing a fully opaque color (such as `Color.Red` or `'#FFFF0000'`) will obscure the material filter effect.

> **NOTE**
>
> The materialColor parameter takes effect on devices of all computing power levels. On high- and medium-computing-power devices, this parameter blends an additional solid color into the material filter. On low-computing-power devices, this parameter serves as the value of the [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor) attribute.

The following example demonstrates the effect of material color tinting for high computing power device balance level: after a semi-transparent `materialColor` is set for the ULTRA_THIN material component, the material presents the corresponding hue while revealing the background content.

<!-- @[material_color](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsImmersiveLightSense/entry/src/main/ets/pages/MaterialColorExample.ets) -->

``` TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MaterialColorExample {
  build() {
    Column() {
      Tabs({ barPosition: BarPosition.End }) {
        TabContent() {
          // Replace $r('app.media.invert') with the image resource file you need.
          Image($r('app.media.invert'))
            .width('100%')
            .height('100%')
            .objectFit(ImageFit.Cover)
        }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'tab1')
          .labelStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
          .iconStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
        )

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'tab2')
          .labelStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
          .iconStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
        )
      }
      .barFloatingStyle({
        adaptToHandedness: true,
        maskHeight: 0,
        systemMaterial: new uiMaterial.ImmersiveMaterial(
          {
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
            // Set the material tinting color.
            materialColor: 'rgba(255, 0, 0, 0.2)',
          }
        )
      })
      .barOverlap(true)
      .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```


![materialColor](figures/material-color.jpg)

## Setting Interactive Effects for Immersive System Material

The immersive system material supports setting interactive deformation and point light effects:

- **Interactive deformation**: Enable interactive deformation through [interactive](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions). When a component is pressed, it produces elastic deformation and automatically recovers after release, enhancing the visual feedback of interaction.
- **Point light effect**: Enable the point light effect through [lightEffect](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions). When the user touches a component, a flowing light effect follows the finger. The effect is enabled when a valid object is passed to `lightEffect`, and disabled when `null` or `undefined` is passed. The `color` field in the object customizes the flowing light color, with the default value `Color.White`.

The following example demonstrates the effects of interactive deformation and point light in the balanced mode of a high computing power device: After `interactive` is set to `true` and a `lightEffect` object is passed, pressing the component causes elastic deformation, and touching it with a finger produces a flowing light follow effect.

<!-- @[material_interactive_light](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsImmersiveLightSense/entry/src/main/ets/pages/MaterialInteractiveLightExample.ets) -->


``` TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MaterialInteractiveLightExample {
  build() {
    Column() {
      Tabs({ barPosition: BarPosition.End }) {
        TabContent() {
          // $r('app.media.invert') needs to be replaced with the image resource file you need.
          Image($r('app.media.invert'))
            .width('100%')
            .height('100%')
            .objectFit(ImageFit.Cover)
        }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'tab1')
          .labelStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
          .iconStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
        )

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_icon_mask_svg'), 'tab2')
          .labelStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
          .iconStyle({ selectedColor: $r('sys.color.brand'), unselectedColor: $r('sys.color.font_primary') })
        )
      }
      .barFloatingStyle({
        adaptToHandedness: true,
        maskHeight: 0,
        systemMaterial: new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          // Enable interactive deformation.
          interactive: true,
          // Set the interactive point light effect to the default color.
          lightEffect: {},
        }),
      })
      .barOverlap(true)
      .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```


![interactiveLight](figures/interactive-light.gif)

## Setting the Shadow Effect for Immersive System Material

The immersive system material has a built‑in shadow effect by default ([applyShadow](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) is true). This default shadow takes precedence over the general [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) attribute, meaning that any custom shadow settings will not take effect when applyShadow is true. To use a custom shadow, set applyShadow to false and then configure the shadow attribute; the default shadow effect of the immersive system material will no longer be applied.

The following shows the effect of setting a custom shadow (for example, a pink shadow) after `applyShadow` is set to `false`. The example for high-computing-power device balance level is as follows:

<!-- @[custom_shadow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsImmersiveLightSense/entry/src/main/ets/pages/CustomShadowExample.ets) -->


``` TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct CustomShadowExample {
  @Builder
  NavigationTitle() {
    Row() {
      Text('Title')
        .fontSize(20)
        .fontWeight(FontWeight.Bold)

      Column()
        .width(50)
        .height(50)
        .borderRadius(25)
        .justifyContent(FlexAlign.Center)
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          applyShadow: false,
          interactive: true,
        }))
        .shadow({ radius: 100, color: Color.Pink })
    }
    .width('100%')
    .justifyContent(FlexAlign.SpaceBetween)
    .padding({ left: 50, right: 50, top: 20 })
  }

  build() {
    Column() {
      Navigation() {
        // Replace $r('app.media.invert') with the image resource file you need.
        Image($r('app.media.invert'))
          .width('100%')
          .height('100%')
          .objectFit(ImageFit.Cover)
      }
      .title({ builder: this.NavigationTitle, height: '100%' })
      // Replace $r('app.media.greyBackground') with the required image resource file.
      .backgroundImage($r('app.media.greyBackground'))
      .backgroundImageSize({ width: '100%', height: '100%' })
    }.width('100%').height('100%')
  }
}
```


![shadowPink](figures/shadowPink.jpg)
