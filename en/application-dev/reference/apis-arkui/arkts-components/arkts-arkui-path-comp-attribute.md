# Path properties/events

In addition to the [universal attributes](arkts-arkui-commonmethod-c.md), the following attributes are supported.

**Inheritance/Implementation:** PathAttribute extends CommonShapeMethod<PathAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands(value: ResourceStr)
```

Sets a string of path commands that comply with the [SVG path syntax](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg-path-syntax). The unit is px. For details about how to convert pixel units, see Pixel Units.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Path for drawing a line.<br>The default value is an empty string.<br>Default unit: px<br>The **undefined** and **null** values are invalid and treated as the default value.<br>**Since:** 20 |
