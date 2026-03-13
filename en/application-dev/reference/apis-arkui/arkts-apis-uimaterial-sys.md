# @ohos.arkui.uiMaterial (System Material) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

This module provides APIs for system materials. Different system materials correspond to different UI effects, including the background color ([backgroundColor](arkui-ts/ts-universal-attributes-background.md#backgroundcolor)), border color ([borderColor](arkui-ts/ts-universal-attributes-border.md#bordercolor)), border width ([borderWidth](arkui-ts/ts-universal-attributes-border.md#borderwidth)), and shadow ([shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow)).

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

``` ts
import { uiMaterial } from '@kit.ArkUI';
```

## MaterialType

Enumerates system material types.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

| Name    | Value| Description             |
| ------ | --- | --------------- |
| NONE | 0 | No system material effect. The corresponding effects are: [backgroundColor](arkui-ts/ts-universal-attributes-background.md#backgroundcolor) and [borderColor](arkui-ts/ts-universal-attributes-border.md#bordercolor) are transparent, [borderWidth](arkui-ts/ts-universal-attributes-border.md#borderwidth) is 0, and there is no [shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow).|
| SEMI_TRANSPARENT | 1 | Semi-transparent system material effect. The corresponding effect is as follows:<br>[backgroundColor](arkui-ts/ts-universal-attributes-background.md#backgroundcolor): #f2f1f3f5 in light mode and #f2303131 in dark mode.<br>[borderColor](arkui-ts/ts-universal-attributes-border.md#bordercolor): [token](../../ui/theme_skinning.md#system-default-token-color-values) value of **theme.colors.compForegroundPrimary** with 10% transparency. <br>[borderWidth](arkui-ts/ts-universal-attributes-border.md#borderwidth): 1 vp.<br>[shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow): ShadowStyle.OUTER_DEFAULT_SM.<br>|

## MaterialOptions

System material options.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

| Name      | Type                                                       | Read-Only| Optional| Description                                                    |
| ---------- | ----------------------------------------------------------- | ---- | ------- | ----------------------------------------------------- |
| type   | [MaterialType](#materialtype)                                   | No| Yes  | Material type.<br>Default value: **MaterialType.NONE**.|

## Material

System material object on the UI.

### constructor

constructor(options?: MaterialOptions)

A constructor used to create a **Material** object.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

**Parameters**

| Name      | Type                                                      | Mandatory| Description                                                        |
| ---------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
|  options      | [MaterialOptions](#materialoptions)                      | No  | System material options, including the material type.<br>Default value: **{type:MaterialType.NONE}**.   |

## Example

### Example 1: Setting the System Material

This example shows how to apply the **Material** object of a semi-transparent material to a component using the [systemMaterial](arkui-ts/ts-universal-attributes-image-effect-sys.md#systemmaterial23) attribute.

``` ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SystemMaterialPage {
  build() {
    Column() {
      Stack() {
        Image($r('app.media.bg1')) // Replace $r('app.media.bg1') with the image resource file you use.
          .width('100%')
          .height('100%')

        Column()
          .width(100)
          .height(50)
          .position({ x: 50, y: 350 })
          .systemMaterial(new uiMaterial.Material({ type: uiMaterial.MaterialType.SEMI_TRANSPARENT })) // Use the semi-transparent system material effect.
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

![systemMaterial](figures/uiMaterial.jpg)
<!--no_check-->