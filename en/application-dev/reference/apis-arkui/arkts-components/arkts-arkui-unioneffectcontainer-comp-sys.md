# UnionEffectContainer (System API)

Defines UnionEffectContainer Component.

## UnionEffectContainer

```TypeScript
UnionEffectContainer(options?: UnionEffectContainerOptions)
```

Specify the construction options for the UnionEffectContainer to create the UnionEffectContainer component.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [UnionEffectContainerOptions](arkts-arkui-unioneffectcontaineroptions-i-sys.md) | No | UnionEffectContainer constructor options. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [UnionEffectContainerOptions](arkts-arkui-unioneffectcontaineroptions-i-sys.md) | Sets the construction options of **UnionEffectContainer**. |

### Enums

| Name | Description |
| --- | --- |
| [UnionMode](arkts-arkui-unionmode-e-sys.md) | Enumerates the union modes. |

## Examples

```TypeScript
### Example 1: Setting the Union Deformation Effect

This example demonstrates how to use the [UnionEffectContainer](#unioneffectcontainer) component to generate a union deformation effect by changing the spacing value or the spacing between descendant components.


```

```TypeScript
### Example 2: Setting Different Types of Union Deformation Effects

This example demonstrates how to use the [unionMode](#unionmode) API to produce different union deformation effects by setting different union types.

The unionMode API is added since API version 26.0.0.
```
