# Hyperlink properties/events

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

The [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md) are supported.

**Inheritance/Implementation:** HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: Color | number | string | Resource)
```

Sets the color of the hyperlink text.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Color of the hyperlink text<br>&lt;!--RP1--&gt;Default value: '#ff0 07dff', indicating blue.&lt;!--RP1End--&gt; |
