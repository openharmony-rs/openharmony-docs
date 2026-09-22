# ArcAlphabetIndexer properties/events

```TypeScript
declare class ArcAlphabetIndexerAttribute extends CommonMethod<ArcAlphabetIndexerAttribute>
```

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** ArcAlphabetIndexerAttribute extends CommonMethod<ArcAlphabetIndexerAttribute>

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

## autoCollapse

```TypeScript
autoCollapse(enable: Optional<boolean>)
```

Sets whether to enable the adaptive collapse behavior for the indexer.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the adaptive collapse behavior for the indexer.<br>Default value: **true**.<br>**true**: Enable the adaptive collapse behavior.<br>**false**: Disable the adaptive collapse behavior. |

## color

```TypeScript
color(color: Optional<ColorMetrics>)
```

Sets the text color of the index items in the normal state.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Text color.<br>Default value: **0xFFFFFF**, displayed as white |

## font

```TypeScript
font(font: Optional<Font>)
```

Sets the default font style of the index items.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| font | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | Yes | Default font style of the index items.<br>Default value:<br>{<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

## itemSize

```TypeScript
itemSize(size: Optional<LengthMetrics>)
```

Sets the size of the index item area.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Size of the index item area. For the circular item area, this represents the diameter of the circle. Percentage values are not supported.<br>Default value: **24.0**<br>Unit: vp |

## onSelect

```TypeScript
onSelect(handler: Optional<OnSelectCallback>)
```

Triggered when an index item is selected. The return value is the index of the selected item.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnSelectCallback](arkts-arkui-arcalphabetindexer-comp-onselectcallback-t.md)&gt; | Yes | Callback used to return the result. |

## popupBackground

```TypeScript
popupBackground(color: Optional<ColorMetrics>)
```

Sets the background color of the pop-up window.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Background color of the pop-up window.<br>Default value: **0xD8404040**, displayed as dark gray with slight transparency |

## popupBackgroundBlurStyle

```TypeScript
popupBackgroundBlurStyle(style: Optional<BlurStyle>)
```

Sets the background blur style of the pop-up window. If this API is not used, the blur is disabled by default. The corresponding value is **NONE** in **BlurStyle**.

> **NOTE:** 

> After configuring the pop-up window background blur style with **popupBackgroundBlurStyle**, avoid applying
> background colors via [popupBackground](#popupbackground).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes | Background blur style of the pop-up window. |

## popupColor

```TypeScript
popupColor(color: Optional<ColorMetrics>)
```

Sets the text color for the pop-up window.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Text color of the pop-up window.<br>Default value: **0xFFFFFF**, displayed as white |

## popupFont

```TypeScript
popupFont(font: Optional<Font>)
```

Sets the font style of the pop-up window.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| font | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | Yes | Font style of the pop-up window.<br>Default value:<br>{<br>size:'19.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

## selected

```TypeScript
selected(index: Optional<number>)
```

Sets the index of the selected item.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Index of the selected item.<br>Default value: **0**<br>This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md). |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ColorMetrics>)
```

Sets the background color of the selected item.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Background color of the selected item.<br>Default value: **0x1F71FF**, displayed as dark blue |

## selectedColor

```TypeScript
selectedColor(color: Optional<ColorMetrics>)
```

Sets the text color of the selected item.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Text color of the selected item.<br>Default value: **0xFFFFFF**, displayed as white |

## selectedFont

```TypeScript
selectedFont(font: Optional<Font>)
```

Sets the font style of the selected item, including size, weight, style, and font family.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| font | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Font&gt; | Yes | Font style of the selected item.<br>Default value: {<br>size:'13.0fp',<br> style: FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

## usePopup

```TypeScript
usePopup(enabled: Optional<boolean>)
```

Sets whether to display the pop-up window.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to display the pop-up window.<br>**true**: yes; **false**: no<br> Default value: **false** |
