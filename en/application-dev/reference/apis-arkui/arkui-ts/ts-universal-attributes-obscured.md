# Obscuring
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-02T11:55:36.836Z -->

When needed, you can obscure content of a component.

>  **NOTE**
>
> - This feature is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## obscured

obscured(reasons: Array&lt;ObscuredReasons&gt;): T

Sets the privacy mask type for component content to obscure the content during screen recording or screen sharing.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                    | Mandatory                                  | Description                                 |
| -----| ------------------------------------------ | ------------------------------------ | ------------------------------------ |
| reasons | Array<[ObscuredReasons](ts-appendix-enums.md#obscuredreasons10)> | Yes | Sets the mask type of the component content to obscure the content in scenarios such as screen recording and screen sharing. Value selection principle: For details, see the [ObscuredReasons](ts-appendix-enums.md#obscuredreasons10) enum. For example, PLACEHOLDER indicates that a placeholder image is used for masking.<br>Default value: [], which means that when no mask reason is set, privacy masking is not applied to the component content.<br>The privacy mask effect takes effect only on the [Image](ts-basic-components-image.md)<!--Del-->, [FormComponent](ts-basic-components-formcomponent-sys.md)<sup>12+</sup>,<!--DelEnd--> and [Text](ts-basic-components-text.md) components.<br>**Note:**<br>To display the privacy mask during image loading, set the width and height of the Image component. If the width and height are not set, the privacy mask effect will not be displayed during image loading.<br>The Text component does not support the privacy mask when a child component is set or a [styled string](ts-universal-styled-string.md) is set. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## Example

This example demonstrates how to obscure the content of **Text** and **Image** components using the **obscured** API.

```ts
// xxx.ets
@Entry
@Component
struct ObscuredExample {
  build() {
    Row() {
      Column() {
        Text('Text not set obscured attribute').fontSize(10).fontColor(Color.Black)
        Text('This is an example for text obscured attribute.')
          .fontSize(30)
          .width('600px')
          .fontColor(Color.Black)
          .border({ width: 1 })
        Text('Image not set obscured attribute').fontSize(10).fontColor(Color.Black)
        // Replace $r('app.media.icon') with the image resource file you use.
        Image($r('app.media.icon'))
          .width('200px')
          .height('200px')
        Text('Text set obscured attribute').fontSize(10).fontColor(Color.Black)
        Text('This is an example for text obscured attribute.')
          .fontSize(30)
          .width('600px')
          .fontColor(Color.Black)
          .border({ width: 1 })
          .obscured([ObscuredReasons.PLACEHOLDER])
        Text('Image set obscured attribute').fontSize(10).fontColor(Color.Black)
        // Replace $r('app.media.icon') with the image resource file you use.
        Image($r('app.media.icon'))
          .width('200px')
          .height('200px')
          .obscured([ObscuredReasons.PLACEHOLDER])
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

![obscured](figures/obscured.png)

