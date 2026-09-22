# EffectComponent (System API)

The **EffectComponent** component defines combined special effects for child components to optimize the special effect drawing performance.

> **NOTE**

> - The APIs provided by this component are system APIs. > > - Currently, this component provides only combined background blur effects for child components. > > - To use this component for combined background blur effects, first replace the **backgroundBlurStyle(BlurStyle)** > attribute of the target child components with **useEffect(true)**.

## EffectComponent

```TypeScript
EffectComponent()
```

Creates an **EffectComponent** component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## EffectComponent

```TypeScript
EffectComponent(options?: EffectComponentOptions)
```

Creates an effect drawing and combination component. If no parameter is passed or the parameter is EffectLayer.None, the background blur effect of child components is combined. If a parameter is specified, the current rendering layer is placed on a special layer.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EffectComponentOptions](arkts-arkui-effectcomponent-comp-effectcomponentoptions-i-sys.md) | No | EffectComponent constructor parameter. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [EffectComponentOptions](arkts-arkui-effectcomponent-comp-effectcomponentoptions-i-sys.md) | Sets the construction parameters of the current EffectComponent, including the rendering layer of the EffectComponent. |

### Enums

| Name | Description |
| --- | --- |
| [EffectLayer](arkts-arkui-effectcomponent-comp-effectlayer-e-sys.md) | Rendering layer of the EffectComponent. |

## Examples

### Example 1: Using the EffectComponent Component

This example demonstrates how to use the EffectComponent component.



```TypeScript
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

### Example 2: Independent Rendering Layer

This example demonstrates how to render the charging text layer.

```TypeScript
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
