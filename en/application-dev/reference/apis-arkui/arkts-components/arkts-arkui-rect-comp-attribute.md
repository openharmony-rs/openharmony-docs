# Rect properties/events

```TypeScript
declare class RectAttribute extends CommonShapeMethod<RectAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md) and [universal drawing attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported:

**Inheritance/Implementation:** RectAttribute extends CommonShapeMethod<RectAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius(value: Length | Array<any>)
```

Sets the radius of the rounded corner. The value range is greater than or equal to 0. This attribute supports dynamic setting of the attribute method through [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). This attribute has an effect similar to that of [radiusWidth](#radiuswidth) and [radiusHeight](#radiusheight). When used together, it takes precedence over **radiusWidth** and **radiusHeight**. The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled based on the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; Array&lt;any&gt; | Yes | Rounded corner radius.<br>Default value: **0** <br>Default unit: vp <br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as [[0, 0], [0, 0], [0, 0], [0, 0]].<br>**Since:** 20 |

## radiusHeight

```TypeScript
radiusHeight(value: Length)
```

Sets the height of the rounded corner. When only **radiusHeight** is set, the height and width of the rounded corner are the same. This attribute has an effect similar to that of [radius](#radius). When used together with **radius**, **radius** takes precedence over this attribute. This attribute supports dynamic setting of the attribute method through [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled based on the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height of the rounded corner. Value range: ≥ 0.<br>Default value: **0** <br>Default unit: vp. <br>The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as the default value.<br>**Since:** 20 |

## radiusWidth

```TypeScript
radiusWidth(value: Length)
```

Sets the width of the rounded corner. When only **radiusWidth** is set, the width and height of the rounded corner are the same. This attribute has an effect similar to that of [radius](#radius). When used together with **radius**, **radius** takes precedence over this attribute. This attribute supports dynamic setting of the attribute method through [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier). The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are handled based on the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the rounded corner. Value range: ≥ 0.<br>Default value: **0** <br>Default unit: vp <br>The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as the default value.<br>**Since:** 20 |
