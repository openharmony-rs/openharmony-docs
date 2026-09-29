# UIGridEvent

```TypeScript
declare interface UIGridEvent extends UIScrollableCommonEvent
```

Represents the return value of the [getEvent('Grid')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-3) method in **frameNode**, which can be used to set scroll events for a **Grid** node.

**UIGridEvent** inherits from [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md).

**Inheritance/Implementation:** UIGridEvent extends [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md)

**Since:** 19

<!--Device-unnamed-declare interface UIGridEvent extends UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIGridEvent extends UIScrollableCommonEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

Sets the callback for the [onDidScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIGridEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIGridEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md) &#124; undefined | Yes | Callback for the **onDidScroll** event. When **undefined** is passed in, the event callback is reset. |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void
```

Sets the callback of the [onScrollIndex](arkts-arkui-grid-comp-attribute.md#onscrollindex) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIGridEvent-setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void--><!--Device-UIGridEvent-setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnGridScrollIndexCallback](arkts-arkui-grid-comp-ongridscrollindexcallback-t.md) &#124; undefined | Yes | Callback for the **onScrollIndex** event. When **undefined** is passed in, the event callback is reset. |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

Sets the callback for the [onWillScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIGridEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIGridEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](arkts-arkui-common-comp-onwillscrollcallback-t.md) &#124; undefined | Yes | Callback for the **onWillScroll** event. When **undefined** is passed in, the event callback is reset. |
