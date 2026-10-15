# AlphabetIndexer properties/events

```TypeScript
declare class AlphabetIndexerAttribute extends CommonMethod<AlphabetIndexerAttribute>
```

When the [width](arkts-arkui-common-comp-commonmethod-c.md#width1) attribute is set to **"auto"**, the width is adaptive. This means that the width will adjust according to the maximum width of the index items.

The default value of the [padding](arkts-arkui-common-comp-commonmethod-c.md#padding) attribute is 4 vp.

The [maxFontScale](arkts-arkui-text-comp-attribute.md#maxfontscale) and [minFontScale](arkts-arkui-text-comp-attribute.md#minfontscale) attributes are both set to a constant value of 1, which means that they do not change with the system font size.

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** AlphabetIndexerAttribute extends CommonMethod&lt;AlphabetIndexerAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class AlphabetIndexerAttribute extends CommonMethod<AlphabetIndexerAttribute>--><!--Device-unnamed-declare class AlphabetIndexerAttribute extends CommonMethod<AlphabetIndexerAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignStyle

```TypeScript
alignStyle(value: IndexerAlign, offset?: Length)
```

Sets the alignment style of the indexer pop-up window.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-alignStyle(value: IndexerAlign, offset?: Length): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-alignStyle(value: IndexerAlign, offset?: Length): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndexerAlign](arkts-arkui-alphabetindexer-comp-indexeralign-e.md) | Yes | Alignment style of the indexer pop-up window. The pop-up window can be displayed on the right or left of the indexer.<br>Default value: **IndexerAlign.END** |
| offset | [Length](../arkts-apis/arkts-arkui-length-t.md) | No | Spacing between the pop-up window and the alphabetic index bar. A value greater than or equal to **0** is valid. If this parameter is set to a value less than **0** or is not set, the spacing is the same as **popupPosition**. When this parameter and [popupPosition](#popupposition) are set at the same time, **offset** takes effect in the horizontal direction, and **popupPosition.y** takes effect in the vertical direction.<br>**Since:** 10 |

## autoCollapse

```TypeScript
autoCollapse(value: boolean)
```

Sets whether to enable the adaptive collapse behavior for the indexer.

When the first index item is **"#"**: Remaining items ≤ 9: Full display mode (all index items are fully displayed); 9 &lt; Remaining items ≤ 13: Adapts between full display and short collapse modes based on the indexer height; remaining items &gt; 13: Adapts between short and long collapse modes based on the indexer height.

When the first index item is not **"#"**: All items ≤ 9: Full display mode (all index items are fully displayed); 9 &lt; All items ≤ 13: Adapts between full display and short collapse modes based on the indexer height; all items &gt; 13: Adapts between short and long collapse modes based on the indexer height.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlphabetIndexerAttribute-autoCollapse(value: boolean): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-autoCollapse(value: boolean): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to auto-collapse or expand the indexer bar.<br>Default value: <br>Before API version 12: **false** <br>Since API version 12: **true** <br>**true**: Enable the adaptive collapse behavior. <br>**false**: Disable the adaptive collapse behavior. |

## color

```TypeScript
color(value: ResourceColor)
```

Sets the text color for unselected items.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-color(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-color(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Text color of unselected items.<br>Default value: **0x99182431**, displayed as a slightly transparent dark blue. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(value: boolean)
```

Sets whether to enable haptic feedback. When enabled, haptic feedback is triggered when a finger touches or slides to select an index item.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlphabetIndexerAttribute-enableHapticFeedback(value: boolean): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-enableHapticFeedback(value: boolean): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable haptic feedback. <br>**true**: To enable haptic feedback. <br>**false**: Not to enable haptic feedback. <br>Default value: **true** <br>To enable haptic feedback, you must declare the **ohos.permission.VIBRATE** permission under **requestPermissions** in the [module.json5](../../../quick-start/module-configuration-file.md) file of the project. <br>"requestPermissions": [{"name": "ohos.permission.VIBRATE"}] |

## font

```TypeScript
font(value: Font)
```

Sets the text style for unselected items.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-font(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-font(value: Font): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style of unselected items.<br>Default value: <br>API version 11 and earlier: <br>{<br>size:'12.0fp', <br> style:FontStyle.Normal, <br> weight:FontWeight.Regular, <br> family:'HarmonyOS Sans'<br>} <br>API version 12 and later: <br>{<br>size:'10.0vp', <br> style:FontStyle.Normal, <br> weight:FontWeight.Medium, <br> family:'HarmonyOS Sans'<br>} |

## itemBorderRadius

```TypeScript
itemBorderRadius(value: number)
```

Sets the radius of the index background border corners in the alphabetic index bar.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlphabetIndexerAttribute-itemBorderRadius(value: number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-itemBorderRadius(value: number): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Radius of the index background border corners in the alphabetic index bar.<br>Default value: **8vp** <br>This parameter cannot be set in percentage. If the value specified is less than **0**, **0** is used. <br>The radius of the index background border corners in the alphabetic index bar is automatically adaptive (radius of the index corners + 4 vp). |

## itemSize

```TypeScript
itemSize(value: string | number)
```

Sets the size of the index item area.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-itemSize(value: string | number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-itemSize(value: string | number): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; number | Yes | Size of the index item area, which is a square, meaning the side length of the square. This attribute cannot be set in percentage. <br>The actual value is restricted by the component size. The maximum width of an index item is the component width minus the left and right [padding](arkts-arkui-common-comp-commonmethod-c.md#padding), and the maximum height of an index item is (component height minus the top and bottom [padding](arkts-arkui-common-comp-commonmethod-c.md#padding))/number of index items. If the input value is less than or equal to 0, the default value is used. <br>Default value: **16.0** <br>Unit: vp |

## onPopupSelect

```TypeScript
onPopupSelect(callback: OnAlphabetIndexerPopupSelectCallback)
```

Triggered when a secondary index item in the pop-up window is selected. The callback parameter is the index of the selected secondary index item. This event is triggered only when [usingPopup](#usingpopup) is set to **true**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-onPopupSelect(callback: OnAlphabetIndexerPopupSelectCallback): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onPopupSelect(callback: OnAlphabetIndexerPopupSelectCallback): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-alphabetindexer-comp-onalphabetindexerpopupselectcallback-t.md) | Yes | Callback used to process the secondary index selection event of the pop-up window. You need to set [usingPopup](#usingpopup) to **true** first.<br>**Since:** 18 |

## onRequestPopupData

```TypeScript
onRequestPopupData(callback: OnAlphabetIndexerRequestPopupDataCallback)
```

Triggered for a secondary index item content event in the pop-up window. The callback parameter is the index of the selected secondary index item. The return value is the secondary index item content to be displayed in the pop-up window.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-onRequestPopupData(callback: OnAlphabetIndexerRequestPopupDataCallback): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onRequestPopupData(callback: OnAlphabetIndexerRequestPopupDataCallback): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-alphabetindexer-comp-onalphabetindexerrequestpopupdatacallback-t.md) | Yes | Callback used to provide the content of the secondary index item in the pop-up window. You need to set [usingPopup](#usingpopup) to **true** first.<br>**Since:** 18 |

## onSelect

```TypeScript
onSelect(callback: OnAlphabetIndexerSelectCallback)
```

Triggered when an index item is selected, with the callback parameter being the index of the currently selected item.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-onSelect(callback: OnAlphabetIndexerSelectCallback): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onSelect(callback: OnAlphabetIndexerSelectCallback): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnAlphabetIndexerSelectCallback](arkts-arkui-alphabetindexer-comp-onalphabetindexerselectcallback-t.md) | Yes | Callback used to process the index item selection event.<br>**Since:** 18 |

## popupBackground

```TypeScript
popupBackground(value: ResourceColor)
```

Sets the background color of the pop-up window.

When this API is not actively called or the parameter **value** is set to **undefined**:

In API version 11 and earlier, the default background color of the pop-up window is **0xFFFFFFFF**, displayed as white.

From API version 12 to API version 24, the default is **#66808080**, displayed as semi-transparent gray.

Starting from API version 26.0.0, if neither [popupBackground](#popupbackground) nor [popupBackgroundBlurStyle](#popupbackgroundblurstyle) is actively called, or both are called with **value** set to **undefined**, the default display on high-computing-power and medium-computing-power devices is the **THICK** style of the immersive system material [ImmersiveStyle](../arkts-apis/arkts-arkui-uimaterial-immersivestyle-e.md), and the default display on low-computing- power devices is a white background.

If **popupBackgroundBlurStyle** is actively called with a valid **value**, the default background color of the pop- up window is **#66808080**, displayed as semi-transparent gray.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupBackground(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupBackground(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the pop-up window. <br>The background blur effect of the pop-up text can affect the background color. You can disable the effect by setting [popupBackgroundBlurStyle](#popupbackgroundblurstyle) to **NONE**. <br> |

## popupBackgroundBlurStyle

```TypeScript
popupBackgroundBlurStyle(value: BlurStyle)
```

Sets the background blur material of the pop-up window. Before API version 26.0.0, when this API is not called, the default is the component's regular material blur, corresponding to **COMPONENT_REGULAR** in **BlurStyle**. Starting from API version 26.0.0, if neither [popupBackground](#popupbackground) nor [popupBackgroundBlurStyle](#popupbackgroundblurstyle) is actively called, or both are called with **value** set to **undefined**, the default display on high-computing-power and medium-computing-power devices is the **THICK** style of the immersive system material [ImmersiveStyle](../arkts-apis/arkts-arkui-uimaterial-immersivestyle-e.md), and the default display on low-computing- power devices is a white background.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlphabetIndexerAttribute-popupBackgroundBlurStyle(value: BlurStyle): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupBackgroundBlurStyle(value: BlurStyle): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md) | Yes | Background blur style of the pop-up window. <br>The background blur effect can affect [popupBackground](#popupbackground). You can disable the effect by setting it to **NONE**. |

## popupColor

```TypeScript
popupColor(value: ResourceColor)
```

Sets the text color for the primary index item in the pop-up window.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Text color of the pop-up window primary index item.<br>Default value: **0xFF007DFF**, displayed as opaque blue. |

## popupFont

```TypeScript
popupFont(value: Font)
```

Sets the text style for the primary index item in the pop-up window.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupFont(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupFont(value: Font): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style of the primary index item in the pop-up window.<br>Default value: <br>{<br>size:'24.0vp', <br> style:FontStyle.Normal, <br> weight:FontWeight.Medium, <br> family:'HarmonyOS Sans'<br>} |

## popupItemBackgroundColor

```TypeScript
popupItemBackgroundColor(value: ResourceColor)
```

Sets the background color for the secondary index item in the pop-up window.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupItemBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupItemBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the pop-up window secondary index item.<br>Default value:<br>API version 11 and earlier: #FFFFFFFF, displayed as white.<br>API version 12 and later: #00000000, displayed as transparent. |

## popupItemBorderRadius

```TypeScript
popupItemBorderRadius(value: number)
```

Sets the radius of the index border corners in the pop-up window.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlphabetIndexerAttribute-popupItemBorderRadius(value: number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupItemBorderRadius(value: number): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Radius of the index background border corners in the pop-up window.<br>Default value: **24vp**. <br>This parameter cannot be set in percentage. If the value specified is less than **0**, **0** is used. <br>The radius of the index background border corners in the pop-up window is automatically adaptive (radius of the index corners + 4 vp). |

## popupItemFont

```TypeScript
popupItemFont(value: Font)
```

Sets the text style for the secondary index item in the pop-up window.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupItemFont(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupItemFont(value: Font): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style of the secondary index item in the pop-up window.<br>Default value: <br>{<br>size:24, <br>weight:FontWeight.Medium <br>} |

## popupPosition

```TypeScript
popupPosition(value: Position)
```

Sets the position of the pop-up window relative to the midpoint of the top edge of the index bar.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupPosition(value: Position): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupPosition(value: Position): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position | Yes | Position of the pop-up window relative to the midpoint of the top edge of the index bar. When set simultaneously with [alignStyle](#alignstyle), the horizontal direction is controlled by the **offset** parameter of [alignStyle](#alignstyle), and **value.y** takes effect in the vertical direction.<br>Default value: **{x: 60.0, y: 48.0}**<br>Unit: vp |

## popupSelectedColor

```TypeScript
popupSelectedColor(value: ResourceColor)
```

Sets the text color for the selected secondary index item in the pop-up window.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupSelectedColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupSelectedColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Text color of the selected secondary index items in the pop-up window.<br>Default value: **#FF182431**, which is dark blue. |

## popupTitleBackground

```TypeScript
popupTitleBackground(value: ResourceColor)
```

Sets the background color for the primary index item in the pop-up window.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AlphabetIndexerAttribute-popupTitleBackground(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupTitleBackground(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color for the primary index item in the pop-up window.<br>Default value: <br>If the pop-up window has only one index: **#00FFFFFF**. <br>If the pop-up window has multiple indexes: **#0c182431**. |

## popupUnselectedColor

```TypeScript
popupUnselectedColor(value: ResourceColor)
```

Sets the text color for the unselected secondary index items in the pop-up window.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-popupUnselectedColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-popupUnselectedColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Text color of the unselected secondary index items in the pop-up window.<br>Default value: **#FF182431**, which is dark blue. |

## selected

```TypeScript
selected(index: number)
```

Sets the index of the selected item. When this attribute and the **selected** attribute in [AlphabetIndexerOptions](arkts-arkui-alphabetindexer-comp-alphabetindexeroptions-i.md) are set at the same time, this attribute has a higher priority.

Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-selected(index: number): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selected(index: number): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the selected item. <br>Value range: [0, [arrayValue](arkts-arkui-alphabetindexer-comp-alphabetindexeroptions-i.md).length – 1] <br>If the index value is out of the range, the default value **0** is used. <br>Default value: **0** |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(value: ResourceColor)
```

Sets the background color of the selected item.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-selectedBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selectedBackgroundColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the selected item.<br>Default value: **0x1A007DFF**, displayed as a semi-transparent blue. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Sets the text color for the selected item.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-selectedColor(value: ResourceColor): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selectedColor(value: ResourceColor): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Selected item text color.<br>Default value: **0xFF007DFF**, displayed as opaque blue. |

## selectedFont

```TypeScript
selectedFont(value: Font)
```

Sets the text style for the selected item.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-selectedFont(value: Font): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-selectedFont(value: Font): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style of the selected item.<br>Default value: <br>API version 11 and earlier: <br>{<br>size:'12.0fp', <br> style:FontStyle.Normal, <br> weight:FontWeight.Regular, <br> family:'HarmonyOS Sans'<br>} <br>API version 12 and later: <br>{<br>size:'10.0vp', <br> style:FontStyle.Normal, <br> weight:FontWeight.Medium, <br> family:'HarmonyOS Sans'<br>} |

## usingPopup

```TypeScript
usingPopup(value: boolean)
```

Sets whether to display the pop-up window.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AlphabetIndexerAttribute-usingPopup(value: boolean): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-usingPopup(value: boolean): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the pop-up window.<br>Default value: **false**. <br>**true**: Display the pop-up window. <br>**false**: Do not display the pop-up window. |

## onSelected

```TypeScript
onSelected(callback: (index: number) => void)
```

Registers the callback for the index item selection event. The callback parameter is the current selected item index.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [onSelect](#onselect)

<!--Device-AlphabetIndexerAttribute-onSelected(callback: (index: number) => void): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerAttribute-onSelected(callback: (index: number) => void): AlphabetIndexerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (index: number) =&gt; void | Yes | Index of the selected item. |
