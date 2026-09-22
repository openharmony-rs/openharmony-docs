# Path properties/events

```TypeScript
declare class PathAttribute extends CommonShapeMethod<PathAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md#common) and [universal drawing attributes](arkts-arkui-common-comp.md#common), the following attributes are supported:

**Inheritance/Implementation:** PathAttribute extends CommonShapeMethod<PathAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## commands

```TypeScript
commands(value: ResourceStr)
```

Sets the command string that complies with the [SVG path syntax](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg-path-syntax), in px. The command string determines the drawing shape and trajectory of the path. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). For details about the pixel unit conversion method, see [Pixel Units](arkts-arkui-common-comp.md#common).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Command string for path drawing. It must comply with the [SVG path syntax](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg-path-syntax), in px. <br>Default value: empty string <br>Abnormal values **undefined** and **null** are processed as the default value.<br>**Since:** 20 |
