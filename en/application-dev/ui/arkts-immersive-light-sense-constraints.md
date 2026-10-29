# Immersive Lighting Power Consumption Optimization
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3a8b0fe553ae5d0b319caef2cc26c9db6a4714f0 translatedAt=2026-10-12T09:17:03.126Z pushedAt=2026-10-12T11:10:48.551Z -->

The immersive light sensing effect is composed of multiple stacked layers of effects such as material filters, refraction, highlights, and shadows. Rendering it consumes GPU resources, and improper use can significantly increase power consumption.

General optimization principle: Use the immersive light sensing effect as a "scarce" visual resource. Control its area and number of layers, and do not keep it fixed over changing content such as videos, animated images, and animations. Follow the power consumption optimization suggestions below to obtain the immersive light sensing experience while reducing the impact on performance and power consumption.

## Controlling the Material Usage Area

The larger the area affected by the immersive system material, the more pixels need to be processed and the higher the power consumption. Avoid using the immersive system material on a single oversized area, and avoid repeatedly using it on a large number of small areas. It is recommended to use it sparingly in the top title bar of Navigation and the bottom Tabs area, and to prioritize limiting the immersive system material to the local areas that need to be highlighted.

> **NOTE**
>
> After immersive light sensing is enabled,
> - The immersive light sensing effect of the specified dialog components ([AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md), [ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md), [CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md), [CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md), [DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md), [TimePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md), [TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md), [SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md), [AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md) popup, and the text menu triggered by long pressing or double-tapping [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) after setting [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9)) can take effect across the entire page.
> - The immersive light sensing effect of the specified dialog interfaces ([PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md), [ArkUI_NativeDialog](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativedialog.md), [@ohos.promptAction (dialog box)](../reference/apis-arkui/js-apis-promptAction.md), [Popup control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md), [Tips control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md), [Menu control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md), [sheet transition](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)) can take effect across the entire page.
> - The immersive light sensing effect of [Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md), [Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md), and [Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md) can take effect across the entire page.
> - For other components, the effect takes effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where `barPosition` is `BarPosition.End`. Setting the immersive light sensing effect in other areas does not take effect.
 

```ts
import { uiMaterial } from '@kit.ArkUI';

// Positive example: Set the immersive system material for a local container in the Navigation title bar. The material takes effect and its area is controllable.
@Entry
@Component
struct MaterialAreaExample {
  @Builder
  NavigationTitle() {
    Column() {
      Text('Card')
    }
    .width(328)
    .height(120)
    .borderRadius(24)
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.REGULAR,
    }))
  }

  build() {
    Column() {
      Navigation() {
        // Page content
      }
      .title({ builder: this.NavigationTitle, height: '100%' })
    }.width('100%').height('100%')
  }
}

// Counterexample: Set the immersive system material for the entire page background outside the title bar's effective range. The area is too large and the material does not take effect.
Column() {
  // ...Entire page content
}
.width('100%')
.height('100%')
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
```

## Avoid Material Nesting

Nesting material effects causes them to be computed repeatedly, which increases power consumption and causes visual interference between layers. In the same subtree, set the immersive system material only once at the outermost layer; do not set it again on inner nodes.

```ts
// Positive example: Set the immersive system material only once at the outermost layer.
Column() {
  Column() {
    Text('Content')
  }
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))

// Counterexample: The immersive system material is set on both the outer and inner layers, resulting in nesting.
Column() {
  Column() {
    Text('Content')
  }
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THIN,
  }))
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
```

## Avoid Overlapping with Blur Effects

The material filter (`materialFilter`) built into the immersive system material already includes a background blur effect. Adding blur properties such as `backgroundBlurStyle` and `backgroundEffect` on top of it is duplicate processing and incurs additional power consumption.

```ts
// Positive example: Use only the immersive system material, which provides the blur effect.
Column() {
  Text('Content')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THICK,
}))

// Counterexample: Set both the immersive system material and background blur, causing duplicate processing.
Column() {
  Text('Content')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THICK,
}))
.backgroundBlurStyle(BlurStyle.COMPONENT_THICK)
```

## Controlling Dialog Size

On high-computing-power devices, when the immersive light intensity is set to strong or balanced, the Dialog and Menu components come with immersive spatial effects such as deformation and flowing light by default (see [immersive spatial effects](arkts-immersive-light-sense-overview.md#immersive-spatial-animation) for details). The larger the dialog area, the higher the rendering overhead of these effects. Therefore, avoid oversized Dialog or Menu components that are nearly full-screen, and keep the dialog size within a reasonable range.

```ts
// Positive example: Keep the dialog content area at a reasonable size.
@CustomDialog
struct NormalSizeDialog {
  controller: CustomDialogController = new CustomDialogController({ builder: NormalSizeDialog({}) })

  build() {
    Column() {
      Text('Dialog content')
    }
    .width(328)
    .height(216)
  }
}

// Counterexample: The dialog content area is nearly full-screen, resulting in high animation rendering overhead.
@CustomDialog
struct FullSizeDialog {
  controller: CustomDialogController = new CustomDialogController({ builder: FullSizeDialog({}) })

  build() {
    Column() {
      Text('Dialog content')
    }
    .width('100%')
    .height('100%')
  }
}
```

## Avoid Using Immersive System Material over Dynamic Content

The refraction and blur effects of immersive system material require real-time sampling of the content behind them. When the background is continuously changing content such as a video or animated image, the material layer must resample and recalculate, significantly increasing power consumption. Avoid overlaying immersive system material on dynamic content such as videos and animated images.

```ts
// Counterexample: Overlay immersive system material on a video. The immersive system material is redrawn while the video is playing.
Stack() {
  Column() {
    // Video
  }
    .width('100%')
    .height('100%')
  Column() {
    Text('Overlay')
  }
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THIN,
  }))
}
```

## Controlling the Scope of Auto Color Inversion

Auto color inversion ([colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)) calculates the inverted color for each color set through the resource interface in the material subtree. The larger the subtree and the more components involved in inversion, the higher the computational cost. You should control the scope of inversion and avoid enabling inversion across a large area that contains lots of text and icons.

```ts
// Positive example: Narrow the inversion scope and enable it only for local areas that require readability.
Column() {
  // ...Most content does not enable inversion.
  Column() {
    Text('Title').fontColor($r('app.color.text'))
  }
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THIN,
    colorInvert: true,
  }))
}

// Counterexample: Enable inversion on the outer layer of a list that contains many child items, so that all child item colors participate in the calculation.
Column() {
  ForEach(this.largeList, (item: string) => {
    Text(item).fontColor($r('app.color.text'))
  })
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
  colorInvert: true,
}))
```

## Keep Material Parameters and Material Area Stable

Frequently modifying material parameters such as style and materialColor, or frequently adding and removing child nodes in the material area, triggers recalculation of the material effect. It is recommended to determine the material parameters at once and keep them stable. The subtree structure inside the material area should also remain as stable as possible.

```ts
// Positive example: Set the material parameters at once and keep them stable.
new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
  materialColor: '#80FF0000',
})

// Counterexample: Frequently modify the material color in a timer, repeatedly triggering material recalculation.
setInterval(() => {
  this.materialColor = this.nextColor()
}, 100)
```

## Avoid Duplicate Shadow Overlay

The immersive system material already provides a shadow through [applyShadow](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) by default. Setting the general [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) attribute additionally not only conflicts with the material effect but also causes duplicate rendering overhead. To customize the shadow, set `applyShadow` to `false` before using `shadow`, so as to avoid the extra overhead caused by duplicate shadow overlay.

```ts
// Positive example: To customize the shadow, first disable the built-in shadow of the immersive system material (applyShadow: false).
Column() {
  Text('Content')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
  applyShadow: false,
}))
.shadow({ radius: 20, color: Color.Black })

// Counterexample: The immersive system material (applyShadow defaults to true) and the custom shadow coexist, causing duplication and conflict.
Column() {
  Text('Content')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
.shadow({ radius: 20, color: Color.Black })
```
