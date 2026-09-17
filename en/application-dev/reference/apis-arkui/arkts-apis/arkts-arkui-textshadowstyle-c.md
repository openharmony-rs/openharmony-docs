# TextShadowStyle

Describes the text shadow style.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: ShadowOptions | Array<ShadowOptions>)
```

A constructor used to create a text shadow style.

The **ShadowOptions** object does not support the **fill** field.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md)&gt; | Yes | Text shadow options. |

## textShadow

```TypeScript
readonly textShadow: Array<ShadowOptions>
```

Text shadow of the styled string.

**Type:** Array&lt;[ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
