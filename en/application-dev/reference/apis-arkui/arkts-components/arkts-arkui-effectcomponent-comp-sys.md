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
| options | [EffectComponentOptions](arkts-arkui-effectcomponentoptions-i-sys.md) | No | EffectComponent constructor parameter. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [EffectComponentOptions](arkts-arkui-effectcomponentoptions-i-sys.md) | Sets the construction parameters of the current EffectComponent, including the rendering layer of the EffectComponent. |

### Enums

| Name | Description |
| --- | --- |
| [EffectLayer](arkts-arkui-effectlayer-e-sys.md) | Rendering layer of the EffectComponent. |

## Examples

```TypeScript
### Example 1: Using the EffectComponent Component

This example demonstrates how to use the EffectComponent component.


```

```TypeScript
### Example 2: Independent Rendering Layer

This example demonstrates how to render the charging text layer.
```
