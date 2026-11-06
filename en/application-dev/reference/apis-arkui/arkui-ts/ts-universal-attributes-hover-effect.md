# Hover Effect
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-01T12:40:02.135Z -->

Sets the mouse hover display effect of a component. It supports multiple hover effect types such as scaling, fade-in/fade-out, and the system default, providing visual feedback when the mouse pointer hovers over a component to help users identify the current interaction area and improve the UI interaction experience.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## hoverEffect

hoverEffect(value: HoverEffect): T

Sets the mouse hover display effect of a component. When hoverEffect is not set, the default hover effect of the component is HoverEffect.Auto. For a component with a hover effect set, the hover effect disappears when the mouse hovers over the component and is pressed; the hover effect is restored when the mouse is released and the mouse pointer remains hovering over the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                            | Mandatory| Description                                                        |
| ------ | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [HoverEffect](ts-appendix-enums.md#hovereffect8) | Yes  | Hover effect of the component.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, which supports chained calls. |

## Example

This example demonstrates how to set the hover effect for components using **hoverEffect**.

```ts
// xxx.ets
@Entry
@Component
struct HoverExample {
  @State isHoverVal: boolean = false

  build() {
    Column({ space: 5 }) {
      Column({ space: 5 }) {
        Text('Scale').fontSize(20).fontColor(Color.Gray).width('90%').position({ x: 0, y: 80 })
        Column()
          .width('80%')
          .height(200)
          .backgroundColor(Color.Gray)
          .position({ x: 40, y: 120 })
          .hoverEffect(HoverEffect.Scale)
          .onHover((isHover: boolean) => {
            console.info(`Scale isHover: ${isHover}`);
            this.isHoverVal = isHover;
          })

        Text('Board').fontSize(20).fontColor(Color.Gray).width('90%').position({ x: 0, y: 380 });
        Column()
          .width('80%')
          .height(200)
          .backgroundColor(Color.Yellow)
          .hoverEffect(HoverEffect.Highlight)
          .position({ x: 40, y: 420 })
          .onHover((isHover: boolean) => {
            console.info(`Highlight isHover: ${isHover}`);
            this.isHoverVal = isHover;
          })
      }
      .hoverEffect(HoverEffect.None)
      .width('100%')
      .height('100%')
      .border({ width: 1 })
      .onHover((isHover: boolean) => {
        console.info('HoverEffect.None');
        this.isHoverVal = isHover;
      })
    }
  }
}
```
![onHover](figures/onHover.gif)
