# Pixel Units
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI provides four pixel units, with vp as the reference data unit.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The following APIs are deprecated since API version 18: vp2px, px2vp, fp2px, px2fp, lpx2px, px2lpx. Directly using these can lead to the issue of [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the [UIContext](../arkts-apis-uicontext-uicontext.md) object using the **getUIContext()** API and then call the[vp2px](../arkts-apis-uicontext-uicontext.md#vp2px12)/[px2vp](../arkts-apis-uicontext-uicontext.md#px2vp12)/[fp2px](../arkts-apis-uicontext-uicontext.md#fp2px12)/[px2fp](../arkts-apis-uicontext-uicontext.md#px2fp12)/[lpx2px](../arkts-apis-uicontext-uicontext.md#lpx2px12)/[px2lpx](../arkts-apis-uicontext-uicontext.md#px2lpx12) API through this object.
>
> - If no UI instance is created, vp2px/px2vp performs conversion using the default screen's virtual pixel ratio. In this case, you can replace vp2px/px2vp/fp2px/px2fp/lpx2px/px2lpx with UIContext. For details, see [Replacing Pixel Unit Conversion APIs with UIContext APIs](../../../ui/arkts-global-interface.md#replacing-pixel-unit-conversion-apis-with-uicontext-apis).


| Name| Description                                                        |
| ---- | ------------------------------------------------------------ |
| px   | Physical pixel unit of the screen.                                          |
| vp   | Pixel unit specific to the screen density. Pixels in this unit are converted into physical pixels of the screen based on the screen pixel density. This unit is used for values whose unit is not specified.<br> **NOTE**<br>The ratio of vp to px is subject to the screen pixel density.|
| fp   | Font pixel, which is similar to vp and varies according to the system font size.|
| lpx  | Logical pixel unit of the window. It is the ratio of the actual screen width to the logical width (configured by [designWidth](../../../quick-start/module-configuration-file.md#pages)). For example, if **designWidth** is set to **720** (default value), then 1 lpx is equal to 2 px for a screen with an actual width of 1440 physical pixels.|

## vp2px<sup>(deprecated)</sup>

vp2px(value: number): number

Converts a value in units of vp to a value in units of px.

> **NOTE**
>
> By default, the virtual pixel ratio of the screen where the current UI instance is located is used for conversion. If the UI instance is unclear, the virtual pixel ratio of the default screen is used instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | Yes  | Converts a value in units of vp to a value in units of px.<br>Value range: (-∞, +∞).|

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Value after conversion.<br>Value range: (-∞, +∞).|

## px2vp<sup>(deprecated)</sup>

px2vp(value: number): number

Converts a value in units of px to a value in units of vp.

> **NOTE**
>
> By default, the virtual pixel ratio of the screen where the current UI instance is located is used for conversion. If the UI instance is unclear, the virtual pixel ratio of the default screen is used instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | Yes  | Converts a value in units of px to a value in units of vp.<br>Value range: (-∞, +∞).|

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Value after conversion.<br>Value range: (-∞, +∞).|

## fp2px<sup>(deprecated)</sup>

fp2px(value: number): number

Converts a value in units of fp to a value in units of px.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | Yes  | Converts a value in units of fp to a value in units of px.<br>Value range: (-∞, +∞).|

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Value after conversion.<br>Value range: (-∞, +∞).|

## px2fp<sup>(deprecated)</sup>

px2fp(value: number): number

Converts a value in units of px to a value in units of fp.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | Yes  | Converts a value in units of px to a value in units of fp.<br>Value range: (-∞, +∞).|

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Value after conversion.<br>Value range: (-∞, +∞).|

## lpx2px<sup>(deprecated)</sup>

lpx2px(value: number): number

Converts a value in units of lpx to a value in units of px.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | Yes  | Converts a value in units of lpx to a value in units of px.<br>Value range: (-∞, +∞).|

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Value after conversion.<br>Value range: (-∞, +∞).|

## px2lpx<sup>(deprecated)</sup>

px2lpx(value: number): number

Converts a value in units of px to a value in units of lpx.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | Yes  | Converts a value in units of px to a value in units of lpx.<br>Value range: (-∞, +∞).|

**Return value**

| Type  | Description          |
| ------ | -------------- |
| number | Value after conversion.<br>Value range: (-∞, +∞).|

## Example

```ts
// xxx.ets
@Entry
@Component
struct Example {
  build() {
    Column() {
      Flex({ wrap: FlexWrap.Wrap }) {
        Column() {
          Text("width(220)")
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220px')")
            .width('220px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
        }.margin(5)

        Column() {
          Text("width('220vp')")
            .width('220vp')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220lpx') designWidth:720")
            .width('220lpx')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width(vp2px(220) + 'px')")
            .width(this.getUIContext().vp2px(220) + 'px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("fontSize('12fp')")
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)

        Column() {
          Text("width(px2vp(220))")
            .width(this.getUIContext().px2vp(220))
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)
      }.width('100%')
    }
  }
}
```

![en-us_image_0000001169582302](figures/en-us_image_0000001169582302.png)
