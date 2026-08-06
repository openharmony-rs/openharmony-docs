# EffectComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=fd10fbb9e5b5e2e1e561a46b9ca4925a29d1a0a3 translatedAt=2026-06-30T12:25:36.268Z pushedAt=2026-07-02T09:00:21.752Z -->

The **EffectComponent** component defines combined special effects for child components to optimize the special effect drawing performance.

>  **NOTE**
>
> - This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.
>
> - The APIs of this module can be used only in the stage model.
>
> - Currently, this component only supports the drawing combination optimization of the background blur effect of child components.
>
> - When performing drawing combination on the background blur effect of a child component, replace the child component's **backgroundBlurStyle(BlurStyle)** attribute with **useEffect(true)**.

## Child Components

Supported

## APIs

### EffectComponent

EffectComponent()

Creates an **EffectComponent** component.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### EffectComponent<sup>20+</sup>

EffectComponent(options?: EffectComponentOptions)

Creates an effect drawing and combination component. If no parameter is passed or the parameter is EffectLayer.None, the background blur effect of child components is combined. If a parameter is specified, the current rendering layer is placed on a special layer.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type       | Mandatory  | Description                                    |
| -------------- | ---------------------------------------- | ---- |  ---------------------------------------- |
| options      | [EffectComponentOptions](#effectcomponentoptions20) | No   |  EffectComponent constructor parameter.              |

## Events

The universal events are not supported.

## Attributes

The universal attributes are supported. Currently, this component only works with the **backgroundBlurStyle** attribute.

## EffectComponentOptions<sup>20+</sup>

Sets the construction parameters of the current EffectComponent, including the rendering layer of the EffectComponent.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                    | Read-only| Optional| Description                                                    |
| ----------- | --------------------------------------- | ---- | ---- | -------------------------------------------------------- |
| effectLayer | [EffectLayer](#effectlayer20)| No   | No   | Rendering layer of the **EffectComponent**.<br/>Default value: **EffectLayer.NONE** |

## EffectLayer<sup>20+</sup>

Rendering layer of the EffectComponent.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Value  | Description        |
| :------------ | :--- | :----------- |
| NONE          | 0    | No special effect layer.  |
| CHARGE_MOTION | 1    | Charging animation layer.|
| CHARGE_TEXT   | 2    | Charging text layer.|

## Example

### Example 1: Using the EffectComponent Component

This example demonstrates how to use the **EffectComponent** component.

```ts
//Index.ets
@Entry
@Component
struct Index {
  build() {
    Stack() {
      Image($r("app.media.example"))
        .autoResize(true)
      EffectComponent() {
        Column({ space: 20 }) {
          // Use backgroundBlurStyle to apply a background blur effect.
          Text("Normal text with backgroundBlurStyle")
            .textAlign(TextAlign.Center)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .backgroundBlurStyle(BlurStyle.Thick)
            .borderRadius(16)
            .width('90%')
            .height('48')

          // Do not apply a background blur effect.
          Text("Normal text without blur effect")
            .textAlign(TextAlign.Center)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .border({ width: 1 })
            .borderRadius(16)
            .width('90%')
            .height('48')

          // Use useEffect to combine drawing of the background blur effect, with blur settings inherited from <EffectComponent>.
          Text("Normal text with useEffect blur 1")
            .textAlign(TextAlign.Center)
            .useEffect(true)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .borderRadius(16)
            .width('90%')
            .height('48')

          // Use useEffect to combine drawing of the background blur effect, with blur settings inherited from <EffectComponent>.
          Text("Normal text with useEffect blur 2")
            .textAlign(TextAlign.Center)
            .useEffect(true)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .borderRadius(16)
            .width('90%')
            .height('48')
        }
        .width('100%')
      }
      .backgroundBlurStyle(BlurStyle.Thin)
    }
    .backgroundColor(Color.Black)
    .width('100%')
    .height('100%')
  }
}
```

![en-us_image_effectcomponent](figures/en-us_image_effectcomponent.png)

### Example 2: Independent Rendering Layer

This example demonstrates how to render the charging text layer.

```ts
@Entry
@Component
struct Index {
  build() {
    Stack() {
      Image($r("app.media.startIcon"))
        .autoResize(true)
      EffectComponent({effectLayer: EffectLayer.CHARGE_TEXT}) {
        Text('CHARGE_TEXT')
          .height('50%')
          .width('100%')
          .fontSize(50)
          .textAlign(TextAlign.Center);
      }
      .backgroundBlurStyle(BlurStyle.Thin)
    }
    .backgroundColor(Color.Black)
    .width('100%')
    .height('100%')
  }
}
```