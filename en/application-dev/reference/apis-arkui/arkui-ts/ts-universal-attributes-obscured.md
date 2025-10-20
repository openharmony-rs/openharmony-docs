# Obscuring
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

When needed, you can obscure content of a component.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

## obscured

obscured(reasons: Array&lt;ObscuredReasons&gt;): T

Sets how the component content is obscured.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**


| Name| Type                                    | Mandatory                                  | Description                                 |
| -----| ------------------------------------------ | ------------------------------------ | ------------------------------------ |
| reasons | Array<[ObscuredReasons](ts-appendix-enums.md#obscuredreasons10)> | Yes| How the component content is obscured.<br>Default value: **[]**<br>This API is only available for the [Image](ts-basic-components-image.md)<!--Del-->, [FormComponent](ts-basic-components-formcomponent-sys.md)<sup>12+</sup>,<!--DelEnd--> and [Text](ts-basic-components-text.md) components.<br>**NOTE**<br>To obscure an image when it is being loaded, you must set the width and height of the **Image** component.<br>Obscuring is not available for **Text** components that have child components or have any [styled string](ts-universal-styled-string.md) configured.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

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
