# Hyperlink properties/events

```TypeScript
declare class HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** HyperlinkAttribute extends CommonMethod&lt;HyperlinkAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>--><!--Device-unnamed-declare class HyperlinkAttribute extends CommonMethod<HyperlinkAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: Color | number | string | Resource)
```

Sets the color of the hyperlink text.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HyperlinkAttribute-color(value: Color | number | string | Resource): HyperlinkAttribute--><!--Device-HyperlinkAttribute-color(value: Color | number | string | Resource): HyperlinkAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Color of the hyperlink text<br><!--RP1-->Default value: '#ff007dff', indicating blue.<!--RP1End--> |
