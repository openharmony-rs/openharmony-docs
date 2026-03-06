# UnionEffectContainer (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
 	 
A shape fusion container, which collects the shapes of all descendant components that use the ancestor fusion effect (ts-universal-attributes-use-union-effect-sys.md#useunioneffect) in the container and applies the collected shapes to the container as the drawing shape of the container.
 	 
>  **NOTE:**
>
> - This component is supported since API version 23. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.
> 
> - Animations can be added to the shape fusion process.
 	 
## Sub-components.

This component can contain child components.

## APIs

### UnionEffectContainer

UnionEffectContainer(options?: UnionEffectContainerOptions)

Creates a shape fusion container component.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type       | Mandatory  | Description                                    |
| -------------- | ---------------------------------------- | ---- |  ---------------------------------------- |
| options      | [UnionEffectContainerOptions](ts-universal-attributes-use-union-effect-sys.md#useunioneffect)| No   |  UnionEffectContainer constructor parameter, which is used to determine the degree of fusion of the collected shapes of descendant components.<br>Default value: **{spacing:0}**              |

## UnionEffectContainerOptions object description

Sets the constructor parameters of UnionEffectContainer.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                                   | Read-Only| Optional| Description                                                    |
| ----------- | --------------------------------------- | ---- | ---------- | ---------------------------------------------- |
| spacing | number | No| Yes | spacing indicates a degree to which a descendant component is fused and deformed. It does not represent the actual spacing. Fusion occurs only when the descendant component that uses the UnionEffectContainer fusion effect of the ancestor component is set and the descendant component is close to a certain extent.<br>**NOTE:**<br>If the spacing is greater than 0 and the descendant components for which the ancestor component UnionEffectContainer fusion effect is set are close to each other to a certain extent, these descendant components start to be fused and deformed with each other, and the fusion and deformation effect is stronger as the distance becomes closer. A larger value indicates that when descendants are close to each other, their fusion starts earlier and is more likely to deform.<br>Default value: 0. In this case, the shapes of the subcomponents are fused together, but there is no deformation effect.<br>Value range: [0, +∞). If the value is less than 0, the value 0 is used.|

## Event

The universal events are supported.

## Properties

Common attributes are supported, and the width and height can be set.

> **NOTE:**
>
> - During the fusion, the container becomes the non-linear deformation effect of stitching, and the border becomes the stitching effect after fusion. Therefore, the capabilities related to the border are affected. Currently, the following border-related attributes support the fusion deformation effect: border [border](ts-universal-attributes-border.md#border), outer border [outline](ts-universal-attributes-outline.md#outline), shadow [shadow](ts-universal-attributes-image-effect.md#shadow), background color [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), and point light source [pointLight](#pointlight). The preceding effect is drawn on the fused shape, which belongs to the drawing part of UnionEffectContainer.
>
> - Set the preceding border-related attributes that support the fusion deformation effect on this component. If the same attribute is set for a descendant component, the settings of the two attributes are independent of each other. The drawing is performed twice, once during the drawing of the UnionEffectContainer control, once in the property drawing of the descendant component itself. Generally, you do not need to set the same attribute that supports the fusion deformation effect in the descendant component that uses the fusion effect of the ancestor component UnionEffectContainer to avoid deterioration of the fusion effect.

### pointLight

pointLight(value: PointLightStyle)

Sets the point light style.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes  | Point light style.|

## Example

### Example 1: Setting the Union Effect

This example demonstrates how to use the [UnionEffectContainer](#unioneffectcontainer) component to generate a union deformation effect by changing the spacing value or the distance between child components.

```ts
//UnionEffectContainerPage.ets
@Entry
@Component
struct UnionEffectContainerPage {
  @State spacing: number = 0;
  @State translateY: number = 0;

  build() {
    Column() {
      Column() {
        UnionEffectContainer({ spacing: 10 }) {
          Column({ space: 50 }) {
            Column()
              .width(100)
              .height(100)
              .margin({ top: 10 })
              .borderRadius(50)
              .useUnionEffect(true)// Set the useUnionEffect attribute to use the blending effect.
              .translate({ y: this.translateY })

            Column()
              .width(200)
              .height(100)
              .useUnionEffect(true)
          }
          .width('100%')
        }
        .width('100%')
        .height('80%')
        .backgroundColor("#2787d9") // Set the attributes supported by the blending effect, such as the background color.

        Row({ space: 30 }) {
          Text("translate:")
          Button('+10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY += 10; // Change the distance between child components.
              });
            })
          Button('-10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY -= 10; // Change the distance of the child component.
              });
            })
        }
        .width('100%')
        .height('20%')
      }.width('90%')
      .height('40%')
      .borderWidth(1)
      .margin({ top: 10 })

      Column() {
        UnionEffectContainer({ spacing: this.spacing }) {
          Column({ space: 50 }) {
            Column()
              .width(100)
              .height(100)
              .margin({ top: 10 })
              .borderRadius(50)
              .useUnionEffect(true) // Set the useUnionEffect attribute to use the blending effect.

            Column()
              .width(200)
              .height(100)
              .useUnionEffect(true)
          }
          .width('100%')
        }
        .width('100%')
        .height('80%')
        .backgroundColor("#2787d9") // Set the attributes supported by the blending effect, such as the background color.

        Row({ space: 30 }) {
          Text("spacing:")
          Button('+20')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.spacing += 20; // Change the spacing of the child component.
              });
            })
          Button('-20')
            .onClick(() => {
              if (this.spacing <= 0 && this.spacing - 20 < 0) {
                return;
              }
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.spacing -= 20; // Change the distance of the child component.
                if (this.spacing < 0) {
                  this.spacing = 0;
                }
              });
            })
        }
        .width('100%')
        .height('20%')
      }.width('90%')
      .height('40%')
      .borderWidth(1)
      .margin({ top: 10 })
    }.width('100%')
    .height('100%')
  }
}
```

![unionEffectContainerDemo](figures/unionEffectContainerDemo.gif)
