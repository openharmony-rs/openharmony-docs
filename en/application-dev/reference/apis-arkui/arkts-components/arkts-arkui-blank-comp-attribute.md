# Blank properties/events

```TypeScript
declare class BlankAttribute extends CommonMethod<BlankAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** BlankAttribute extends CommonMethod<BlankAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor)
```

Sets the fill color of the **Blank** component. This attribute can be dynamically set using [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color to fill the blank.<br>Default value: **Color.Transparent** <br>Invalid values are treated as the default value. |
