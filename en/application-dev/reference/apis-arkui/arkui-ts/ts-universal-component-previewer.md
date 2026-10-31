# Component Preview

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xin11112-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=e9ef5d5b6b2360db0a0bb679b4d8c44c6096ceda translatedAt=2026-09-02T12:18:44.967Z -->

Component preview enables you to preview the UI effect of individual custom components.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  For details about usage, see [Component Preview](../../../ui/ui-ide-previewer.md#component-preview).

## @Preview Decorator

The @Preview decorator decorates custom components for preview.

>  **NOTE**
>
>  This API is supported in ArkTS widgets, though component preview itself is not supported in ArkTS widgets.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## PreviewParams<sup>9+</sup>

Implements a configuration object for @Preview parameters.

Defines preview device attributes such as device type and screen state.

>  **NOTE**
>
>  In PreviewParams, only input parameters that match the defined parameter types are supported. Otherwise, all @Preview parameters are set to default values.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type  | Read-Only| Optional| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| title | string | No | Yes | Title of the component preview. The default value is the custom component name. Only English letters and digits are supported. Chinese characters and special characters are not supported. |
| width | number | No | Yes | Width of the preview device, in px. The default value is 1080px. The value is an integer within [20, 3000]. |
| height | number | No | Yes | Height of the preview device, in px. The default value is 2340px. The value is an integer within [20, 3000]. |
| locale| string | No | Yes | Language and region of the preview device, for example, zh_CN and en_US. The default value is zh_CN. |
| colorMode | string | No | Yes | Light or dark mode to display. The value can be light or dark. The default value is dark for TV devices and light for other devices. Wearable devices support only dark. |
| deviceType | string | No | Yes | Device type on which the component preview is rendered. The default value is Phone. For details about the device type enums, see [deviceTypes tag](./../../../quick-start/module-configuration-file.md#devicetypes). |
| dpi | number | No | Yes | Screen DPI of the preview device. The default value is 480. The value is an integer within [120, 640]. |
| orientation | string | No| Yes| Screen orientation of the preview device. Options: **portrait** (default), **landscape**.|
| roundScreen | boolean | No| Yes| Whether the preview screen is circular. Default value: **false**. **true**: circular. **false**: non-circular.|

## Example.

This example demonstrates @Preview usage with and without parameters.

```ts
@Entry
@Preview
@Component
struct Index {
  @State message: string = 'default Preview';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }
}

@Preview({
  title: 'PreviewParams',
  width: 540,
  height: 1170
})
@Component
struct Test {
  @State message: string = 'PreviewParams';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontSize(40)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
    .width('100%')
  }
}
```
