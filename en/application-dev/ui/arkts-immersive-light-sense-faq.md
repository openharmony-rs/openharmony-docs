# FAQs About Immersive Lighting
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=218b1a6f02f9e47e32daf87fcc74c389c1461599 translatedAt=2026-10-28T11:43:05.972Z pushedAt=2026-10-29T08:35:58.572Z nl=1 -->

This document provides common issues and solutions encountered during the development of immersive lighting. For a complete introduction and development guide to immersive lighting, see [Immersive Lighting Overview](arkts-immersive-light-sense-overview.md).

<!--RP1--><!--RP1End-->

## No Material Effect Is Visible After Setting Immersive System Material for a Component

### Component Outside the Immersive Lighting Effective Scope

**Symptom**

- After immersive lighting is enabled, the component does not display the immersive lighting effect.
- The log contains the following message: Material inactive: out of scope. Use component in navigation title bar or Tabbar.

**Possible Causes**

After immersive lighting is enabled,
- The immersive lighting effect of the specified dialog components ([AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md), [ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md), [CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md), [CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md), [DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md), [TimePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-timepicker-dialog.md), [TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md), [SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md), the [AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md) dialog, and the text menu triggered by long press or double tap after setting [copyOption](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#copyoption9) on [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)) can take effect on the full page.
- The Immersive Light Sense effect of the specified dialog APIs ([PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md), [ArkUI_NativeDialog](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativedialog.md), [@ohos.promptAction (Dialog)](../reference/apis-arkui/js-apis-promptAction.md), [Popup Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md), [Tips Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-tips.md), [Menu Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md), and [Sheet Transition](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)) can take effect on the full page.
- The Immersive Light Sense effect of [Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md), [Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md), and [Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md) can take effect on the full page.
- Other components take effect only in the Navigation/NavDestination title bar or in the bottom TabBar of horizontal Tabs where `barPosition` is `BarPosition.End`. Setting the Immersive Light Sense effect in other areas does not take effect.

**Answer**

Place the component that requires the immersive lighting in the Navigation/NavDestination title bar, or in the bottom TabBar of horizontal Tabs where barPosition is BarPosition.End.

If the effective scope requirement cannot be met, use universal attributes such as [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor) instead of the material effect.

**Example**

The following example shows the display effect of enabling immersive lighting in the Navigation title bar and in the Navigation content area, respectively. The Column in the Navigation title bar takes effect normally when immersive lighting is enabled. The Column component in the Navigation content area does not take effect because it is not located in the Navigation title bar or the bottom TabBar.
 
<!-- @[material_scope_adapt](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsImmersiveLightSense/entry/src/main/ets/pages/MaterialScopeAdaptExample.ets) -->

``` TypeScript
import { CircleShape, TitleBarType, uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MaterialScopeAdaptExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  @State titleHeight: number = 140;

  @Builder
  NavigationTitle() {
    Row() {
      // Replace $r('app.string.title_bar') with the actual resource file. In this example, the value of this resource file is "Title Bar".
      Text($r('app.string.title_bar'))
        .fontColor('#182431')
        .fontSize(30)
        .lineHeight(41)
        .fontWeight(700)
      Blank()
      Column() {
        SymbolGlyph($r('sys.symbol.a_3d_square_fill'))
      }
      .width(50)
      .height(50)
      .clipShape(new CircleShape({
        width: 50,
        height: 50
      }))
      .justifyContent(FlexAlign.Center)
      .backgroundColor(Color.Transparent)
      // Enable immersive lighting in the Navigation title bar. Within the effective range, the immersive lighting effect takes effect.
      .systemMaterial(new uiMaterial.ImmersiveMaterial({
        style: uiMaterial.ImmersiveStyle.THIN,
      }))
    }
    .alignItems(VerticalAlign.Center)
    .width('100%')
    .padding(16)
    .height(this.titleHeight)
  }

  build() {
    Column() {
      Navigation() {
        Column() {
          Row() {
            // Replace $r('app.string.content_area') with the actual resource file. In this example, the value of this resource file is "Content Area".
            Text($r('app.string.content_area'))
              .fontColor('#182431')
              .fontSize(30)
              .lineHeight(41)
              .fontWeight(700)

            Blank()

            Column() {
              SymbolGlyph($r('sys.symbol.a_3d_square_fill'))
            }
            .width(50)
            .height(50)
            .clipShape(new CircleShape({
              width: 50,
              height: 50
            }))
            .justifyContent(FlexAlign.Center)
            .backgroundColor(Color.Transparent)
            // Enable immersive lighting in the Navigation content. Outside the effective range, the immersive lighting effect does not take effect.
            .systemMaterial(new uiMaterial.ImmersiveMaterial({
              style: uiMaterial.ImmersiveStyle.THIN,
            }))
          }
          .width('100%')
          .borderRadius(16)
        }
        .width('100%')
        .height('100%')
        .padding(16)
        .backgroundColor('#FFFFFF')
        .linearGradient({
          angle: 0,
          colors: [
            ['#004AAF', 0.0],
            ['#2787D9', 0.5],
            ['#F0FAFF', 1.0]
          ]
        })
        .justifyContent(FlexAlign.Center)
        .alignItems(HorizontalAlign.Center)
      }
      .title({ builder: this.NavigationTitle, height: this.titleHeight }, { barStyle: BarStyle.STACK })
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```


<!--Del-->   <!--DelEnd-->

### Background Color or Background Blur Obscures the Material Effect

**Symptom**

After calling the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) API to enable immersive lighting for a component, the component's visual appearance does not change and still displays a solid-color background or no material effect at all.

**Possible Causes**

The visual layer of immersive lighting is positioned below the component's [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor), [backgroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundblurstyle9), and other attributes. If an opaque background color or background blur style is set simultaneously, these properties will overlay the material layer, blocking the material effect from being visible.

**Solution**

- Set the component's background color to transparent (`Color.Transparent`) or remove the background color setting.
- Remove background blur styles such as [backgroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundblurstyle9) to prevent the blur effect from covering the material layer.

**Code Example**

```ts
// Incorrect approach: an opaque background color overlays the material layer, making the material effect invisible
Column() {
  Text('Immersive light')
}
.width(328)
.height(56)
.borderRadius(28)
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
}))
.backgroundColor(Color.White)
// Recommended approach: set the background color to transparent to ensure the material effect is visible
Column() {
  Text('Immersive light')
}
.width(328)
.height(56)
.borderRadius(28)
.backgroundColor(Color.Transparent)
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
}))
```

### CustomDialog Does Not Apply the Immersive System Material Effect

**Symptom**

- For custom popups created through [openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12) and [openCustomDialogWithController](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18), the immersive system material effect does not take effect after the `systemMaterial` attribute is passed.
- When [customStyle](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions) of CustomDialog is set to `true`, the immersive system material effect does not take effect on the popup.

**Possible Causes**

If you create a custom popup using `openCustomDialog` or `openCustomDialogWithController`, or set the `customStyle` attribute of the popup to `true`, the popup backplate is customized by you, and adapting the immersive system material to this scenario is not currently supported.

**Answer**

Adapting the immersive system material to the custom popup backplate is not supported.

If you have such a requirement, use other similar APIs, such as [openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12-1).

**Code Example**

The following code shows how to create a custom popup using the [openCustomDialog](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12-1) API and apply the immersive system material effect.

<!-- @[open_custom_dialog_with_system_material_set_material](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/opencustomdialog/openCustomDialogWithSystemMaterial.ets) -->

```ts
Button('Click Me')
  .fontSize(30)
  .onClick(() => {
    this.getUIContext()
      .getPromptAction()
      .openCustomDialog({
        builder: () => {
          this.customDialogComponent()
        },
        systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.ULTRA_THICK })
      })
  })
```

## Component Border Displays Colors from the Surrounding Background After Setting Immersive System Material

**Symptom**

After setting immersive system material for a component, the component's border area displays colors from the surrounding background image or background color, rather than the expected border effect.

**Possible Causes**

This is a normal optical behavior of immersive system materials. The immersive lighting visual effect has refractive properties that cause surrounding content to refract through the material layer into the component's border area. This refraction effect is an important part of the material's transparency and layering, and is particularly noticeable with thinner material styles such as ULTRA_THIN and THIN.

**Solution**

- Use thicker material styles (such as REGULAR, THICK, or ULTRA_THICK) to reduce material transparency and thereby minimize the refraction effect.
- Add a [materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) overlay to the material layer to reduce the visibility of refraction by blending in a semi‑transparent color.

## Material Effect Disappears After an Opaque Color Is Passed to materialColor

**Symptom**

After passing a color to the [materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter of an immersive system material, the material effect completely disappears and only a solid‑color background is displayed.

**Possible Causes**

The [materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter is used to blend an additional solid color layer on top of the material filter [materialFilter](../reference/apis-arkui/arkui-ts/ts-universal-attributes-filter-effect.md#materialfilter23). This color needs to have a certain level of transparency. If a fully opaque color (such as `Color.Red` or `'#FFFF0000'`) is passed, it will obscure the material filter effect.

**Solution**

Pass a color value with transparency to [materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions).

> **NOTE**
>
> The [materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter takes effect on devices of all computing power tiers. On high‑ and medium‑tier devices, it blends an additional solid color layer over the material filter; on low‑tier devices, it serves as the [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor) attribute.

**Code Example**

```ts
// Incorrect usage: a solid opaque color blocks the material effect
new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
  materialColor: Color.Red, // Opaque, the material filter effect is completely blocked
})

// Recommended usage: use a color with transparency
new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
  materialColor: '#80FF0000', // Red with 50% transparency
})
```

## Immersive Light Sense Effect Differs Significantly on Low‑Tier Devices Compared to High‑Tier Devices

**Symptom**

When running the application on low‑tier devices, the visual effect of immersive system materials differs significantly from high‑tier devices, and some material parameter settings do not take effect.

**Possible Causes**

The effect of immersive system material is automatically adapted based on the device's computing power tier. On high and medium computing power devices, it affects the [materialFilter](../reference/apis-arkui/arkui-ts/ts-universal-attributes-filter-effect.md#materialfilter23) effect and shadow effect; on low computing power devices, it affects only the background color, border color, border width, and shadow effect. In addition, the material [style](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) and automatic color inversion [colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameters take effect only on high and medium computing power devices. Setting these two parameters on low computing power devices does not produce any visual difference.

**Solution**

This is a system-level adaptive behavior. You do not need to write differentiated code for devices of different tiers; immersive lighting automatically ensures smooth operation on devices of all tiers.

## Text Color Does Not Change After Enabling Automatic Color Inversion

**Symptom**

After enabling the [colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) automatic color inversion feature for immersive system materials, the color of the text inside the component does not automatically adapt to the background color.

**Possible Causes**

For automatic color inversion to take effect, the following conditions must be met simultaneously:

- The device computing power tier must be high or medium. On low computing power devices, automatic color inversion does not produce a visual difference.
- The material style must be THIN or ULTRA_THIN. It does not take effect under REGULAR, THICK, or ULTRA_THICK styles.
- The system's immersive lighting intensity configuration affects the inversion trigger threshold. The thinner the immersive system material and the stronger the system's immersive lighting setting, the more likely automatic color inversion is triggered.
- Automatic color inversion takes effect only for color values set through resource interfaces, including the [fontColor](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#fontcolor) attribute of the [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) component, the [fontColor](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#fontcolor) attribute of the [Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md) component, the [fontColor](../reference/apis-arkui/arkui-ts/ts-basic-components-symbolGlyph.md#fontcolor) attribute of the [SymbolGlyph](../reference/apis-arkui/arkui-ts/ts-basic-components-symbolGlyph.md) component, the [fillColor](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#fillcolor) attribute of the [Image](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md) component, and the color attributes of components such as TextInput, TextArea, Chip, ChipGroup, SegmentButton, and Swiper. For the complete list of attributes that take effect, see the [colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter description. Hardcoded color values in the code (such as `Color.White` and `'#FFFFFFFF'`) do not trigger automatic color inversion.

**Solution**

1. Ensure that the material style is THIN or ULTRA_THIN.
2. Ensure that the text color is set via resource interfaces (such as `$r('app.color.xxx')`), rather than hard‑coded color values.
3. Increase the system's immersive light configuration and observe the effect.

## Shadow Effect Does Not Behave as Expected When Both shadow Attribute and Immersive System Material Are Set

**Symptom**

After setting both the [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) universal attribute and immersive system material for a component, the shadow effect displays the immersive system material's built-in shadow style, and the custom shadow parameters do not take effect.

**Possible Causes**

When the [applyShadow](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) parameter of the immersive system material is **true** (default value), the shadow effect in the material takes effect fixedly and takes precedence over the [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) universal attribute. In this case, the custom shadow settings do not take effect. When this parameter is **false**, the [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) universal attribute takes effect, and the material's shadow effect does not take effect.

**Solution**

- If you need to use the shadow effect that comes with the immersive system material, you do not need to set the **shadow** attribute additionally.
- If you need to use a custom **shadow** universal attribute, set [applyShadow](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions) to **false**.

**Code Example**

```ts
// Disable the material shadow and use a custom shadow.
new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
  applyShadow: false,
})
```

## Component Style Appears Abnormal After Setting the Immersive System Material via the systemMaterial Universal Attribute

**Symptom**

After setting the immersive system material through the universal attribute [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial), the component's background color, border, and other styles do not display as expected.

**Possible Causes**

When setting the immersive system material through the universal attribute, if [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) is placed before other style attributes, the material effect priority may not match expectations.

**Solution**

Set [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) after other style attributes (such as background color, border, shadow, etc.). When setting the immersive system material through component options parameters (such as **Toast**'s [ShowToastOptions](../reference/apis-arkui/js-apis-promptAction.md#showtoastoptions), **Popup**'s [PopupOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions), etc.), the order does not need to be considered.

**Code Example**

```ts
// Recommended: Set other attributes first, then set systemMaterial.
Column() {
  Text('Recommend')
}
.width(328)
.height(56)
.borderRadius(28)
.justifyContent(FlexAlign.Center)
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
```

## Dialog or Toast Components Do Not Display Material Effects by Default

**Symptom**

In [DEFAULT](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) mode, components such as [Dialog](arkts-base-dialog-overview.md) and [Toast](arkts-create-toast.md) do not display the visual effect of immersive system material.

**Possible Causes**

[DEFAULT](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate) is the default enabling mode for immersive system materials. In this mode, components such as [Dialog](arkts-base-dialog-overview.md), [Toast](arkts-create-toast.md), and [AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md) will only enable immersive system materials by default when no background color, blur parameters, or shadow parameters are set. If you set attributes such as [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor), [backgroundBlurStyle](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundblurstyle9), or [shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow) for these components, immersive system material will not be enabled by default.

**Solution**

- Remove conflicting property settings (such as **backgroundColor**, **backgroundBlurStyle**, and **shadow**) to allow the material effect to be enabled by default.
- In ENABLE mode, immersive system material styles have higher priority than the component's own background color, blur, shadow, and border styles, and more components enable the immersive system material by default.
- To use the immersive system material while retaining existing properties, actively set it via the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) attribute.


## Inconsistency Between the Material Rendering Area and the Component Visibility Area

**Symptom**

After the immersive system material is set for a component, the material rendering area is inconsistent with the component visibility area.

- The visible area of Checkbox is a 40\*40 circle, while the material rendering area is a 40\*40 rectangle.

  <!--Del-->   <!--DelEnd-->

- The visible area of the Text component is the text content, while the material rendering area is a 100\*40 rectangle.

  <!--Del-->   <!--DelEnd-->

- The visible area of the Progress component is capsule-shaped, while the material rendering area is a 100\*40 rectangle.

  <!--Del-->   <!--DelEnd-->

**Possible Causes**

The material rendering area is determined by the component layout area, while the component visibility area is the area where content is actually rendered, which may differ from the layout area, causing the two to be inconsistent.

**Answer**

Use the [width](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#width), [height](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#height), and [borderRadius](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderradius) APIs to keep the component visibility area consistent with the material rendering area.

> **NOTE**
>
> The **Text** component does not support applying immersive system materials to text content.

**Code Example**

```ts
// Example of material rendering area inconsistent with component visibility area
Row() {
  Text('Checkbox component:')
    .fontColor(Color.Black)
  Checkbox()
    .width(40)
    .height(40)
    .borderWidth(1)
    .borderColor(Color.Blue)
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      interactive: true
    }))
}
Row() {
  Text('Text component:')
    .fontColor(Color.Black)
  Text("hello")
    .width(100)
    .height(40)
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      interactive: true
    }))
}

Row() {
  Text('Progress component:')
    .fontColor(Color.Black)
  Progress({value: 40, type: ProgressType.Capsule})
    .width(100)
    .height(40)
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      interactive: true
    }))
}

// Example of material rendering area consistent with component visibility area
Row() {
  Text('Progress component:')
    .fontColor(Color.Black)
  Progress({value: 40, type: ProgressType.Capsule})
    .width(100)
    .height(40)
    .borderRadius(20) // Set the borderRadius attribute to make the material rendering area consistent with the component visibility area.
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      interactive: true
    }))
}
```

## Display Layer Issue of Material Effects

**Symptom**

When both the immersive system material and a background color are set for a component, the material effect is covered. For example, after a background color is set for the TextArea component, it covers the material effect.

<!--Del-->   <!--DelEnd-->

**Possible Causes**

The background color of a self-drawn component applies to the content layer, while the material effect applies to the backplate layer. Because the content layer is above the backplate layer, the material effect is covered by the content layer.

**Answer**

It is not recommended to use the immersive system material together with the background color [backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor) API.

> **NOTE**
>
> The immersive system material cannot be drawn on the content layer.

**Code Example**

```ts
// Example of display layer issue of material effect
Row() {
  Text('TextArea component:')
    .fontColor(Color.Black)
  TextArea()
    .width(100)
    .height(40)
    .backgroundColor('#cc999999') // It is not recommended to use the immersive system material and the background color API at the same time.
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      interactive: true
    }))
}
```
