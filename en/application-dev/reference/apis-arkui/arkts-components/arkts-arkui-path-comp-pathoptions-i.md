# PathOptions

```TypeScript
declare interface PathOptions
```

Describes the options of the path.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands?: ResourceStr
```

Command string for path drawing, complying with the [SVG Path Syntax](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg-path-syntax), in px.

Default value: empty string

An abnormal value is processed as the default value.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

Height of the rectangle where the path is located. The value range is ≥ 0.

If the value is an abnormal value or is not set, the height is automatically calculated based on the path content.

Default unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

Width of the rectangle where the path is located. The value range is ≥ 0.

If the value is an abnormal value or is not set, the width is automatically calculated based on the path content.

Default unit: vp

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
