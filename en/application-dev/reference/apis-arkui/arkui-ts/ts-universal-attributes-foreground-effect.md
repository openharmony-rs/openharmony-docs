# Foreground Effect
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e10e7def4863f4f964c4d0cb425b7650081cb83e translatedAt=2026-09-01T12:36:58.099Z -->

Sets the foreground attributes of a component and applies a blur effect to the foreground content of the component based on the blur radius parameter.

>  **NOTE**
>
> - This feature is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## foregroundEffect

foregroundEffect(options: ForegroundEffectOptions): T

Sets the foreground blur effect of a component. The effect takes effect only within the component scope. When this API is used together with backgroundEffect, blur, or other APIs, the effect beyond the component scope does not take effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                |
| ------ | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| options | [ForegroundEffectOptions](#foregroundeffectoptions) | Yes | Foreground effect of the component, including the blur radius. The effect takes effect only within the component scope. When used together with APIs such as backgroundEffect and blur, the effect beyond the component scope does not take effect. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## ForegroundEffectOptions

Foreground effect parameters, used to configure the blur radius of the component foreground and control the blur degree of the foreground content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       |   Type        |   Read-Only|   Optional|  Description                       |
| ----         |  ----         |   ---- |   ---- | --------------------------  |
| radius       | number        |   No   |   No   |   Blur radius. After it is set, the component foreground presents a blur effect. The larger the value, the higher the blur degree. Value range: [0, +∞), where 0 means no blur effect. Negative values are automatically corrected to 0. It takes effect only within the component scope. When used with effect APIs such as backgroundBlur, the effect beyond the component scope does not take effect.     |

## Example

This example demonstrates how to set the foreground attributes through the foregroundEffect API.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  build() {
    Row() {
      // Replace $r('app.media.icon') with the image resource file required by the developer.
      Image($r('app.media.icon'))
          .width(100)
          .height(100)
          // Set the foreground blur effect with a blur radius of 20.
          .foregroundEffect({ radius: 20 })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

Below is how the component looks with the foreground effect applied.

**radius** indicates the blur radius. A larger value creates a more blurred effect.

![foregroundColor_circle](figures/foregroundEffect.jpg)
