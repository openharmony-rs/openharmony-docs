# Render Fit
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-02T12:05:24.104Z -->

Determines how the component content in the final state of the animation is filled on the component during the width and height animation process. It applies to scenarios where the content fill mode of the animation needs to be controlled, such as card expansion and dialog box scaling.

>  **NOTE**
>
> - This feature is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## renderFit

renderFit(fitMode: RenderFit): T

Sets the content fill mode of the component during the width and height animation process. During the width and height animation process, **renderFit** determines how the content in the final state of the animation is aligned and scaled with the component at its intermediate size. If this attribute is not set, the content size in the final state of the animation is retained, and the content is always aligned with the top-left corner of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Parameters**

| Name | Type                           | Mandatory| Description                                                        |
| ------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| fitMode | [RenderFit](ts-appendix-enums.md#renderfit10) | Yes | Sets the content fill mode of the component during the width and height animation process. For details, see [RenderFit](ts-appendix-enums.md#renderfit10). For a SURFACE-type XComponent component whose background color is set to opaque pure black, only RenderFit.RESIZE_FILL is supported before API version 18. If this parameter is not set, the content size at the end of the animation is retained by default and aligned with the upper left corner of the component (RenderFit.TOP_LEFT). |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## renderFit<sup>18+</sup>

renderFit(fitMode: Optional\<RenderFit>): T

Sets the content fill mode of the component during the width and height animation process. If this attribute is not set, the default value is **RenderFit.TOP_LEFT**, which retains the content size in the final state of the animation and keeps the content aligned with the top-left corner of the component. For an **XComponent** of the TEXTURE or SURFACE type, when the **renderFit** attribute is not set, the default value is **RenderFit.RESIZE_FILL**. Compared with [renderFit](#renderfit), the **fitMode** parameter additionally supports the **undefined** type. When the value of **fitMode** is **undefined**, the effect of **RenderFit.TOP_LEFT** is restored. For an **XComponent** of the TEXTURE or SURFACE type, the effect of **RenderFit.RESIZE_FILL** is restored.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Parameters**

| Name | Type                                      | Mandatory| Description                                                        |
| ------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| fitMode | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[RenderFit](ts-appendix-enums.md#renderfit10)> | Yes | Sets the content fill mode of the component during the width and height animation process.<br>When the value of fitMode is undefined, the effect of RenderFit.TOP_LEFT is restored, that is, the content fill mode keeps the component aligned with the top-left corner. For XComponent components of the TEXTURE and SURFACE types, the effect of RenderFit.RESIZE_FILL is restored. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

>  **NOTE**
>
>  For an [XComponent](ts-basic-components-xcomponent.md) of the TEXTURE or SURFACE type, when the **renderFit** attribute is not set, the default value is **RenderFit.RESIZE_FILL**.
>
> For an [XComponent](./ts-basic-components-xcomponent.md) of the SURFACE type, the background color is set to opaque pure black. Before API version 18, its **renderFit** universal attribute supports only **RenderFit.RESIZE_FILL**. Setting other **RenderFit** enum values does not take effect, and the component is still rendered in the **RenderFit.RESIZE_FILL** mode. Since API version 18, all **RenderFit** enum values are supported.
>
>  For an **XComponent** created using the [ArkUI NDK APIs](../../../ui/ndk-access-the-arkts-page.md), the attribute getter [getAttribute](../capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute) cannot be used to obtain its **renderFit** attribute value.
>
>  The preceding notes also apply to the [renderFit](#renderfit) API.

## Example

This example demonstrates how to set different content fill modes for a component during width and height animations through the **renderFit** attribute.

```ts
// xxx.ets
@Entry
@Component
struct RenderFitExample {
  @State currentWidth: number = 100;
  @State currentHeight: number = 30;
  isExpanded: boolean = true;

  build() {
    Column() {
      Text('Hello')
        .width(this.currentWidth)
        .height(this.currentHeight)
        .borderWidth(1)
        .textAlign(TextAlign.Start)
        .renderFit(RenderFit.LEFT) // Set the renderFit to LEFT. During the animation process, the final-state content stays left-aligned with the component.
        .margin(20)

      Text('Hello')
        .width(this.currentWidth)
        .height(this.currentHeight)
        .textAlign(TextAlign.Center)
        .borderWidth(1)
        .renderFit(RenderFit.CENTER) // Set the renderFit to CENTER. During the animation process, the final-state content stays center-aligned with the component.
        .margin(20)

      Button('animate')
        .onClick(() => {
          this.getUIContext()?.animateTo({ curve: Curve.Ease }, () => {
            if (this.isExpanded) {
              this.currentWidth = 150;
              this.currentHeight = 50;
            } else {
              this.currentWidth = 100;
              this.currentHeight = 30;
            }
            this.isExpanded = !this.isExpanded;
          })
        })
    }.width('100%').height('100%').alignItems(HorizontalAlign.Center)
  }
}
```

![renderfit](figures/renderfit.gif)
