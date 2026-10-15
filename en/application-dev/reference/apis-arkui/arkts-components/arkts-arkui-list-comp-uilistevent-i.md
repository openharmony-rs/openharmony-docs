# UIListEvent

```TypeScript
declare interface UIListEvent extends UIScrollableCommonEvent
```

Represents the return value of the [getEvent('List')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent2) method in **frameNode**, which can be used to set scroll events for a **List** node.

**UIListEvent** inherits from [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md).

**Inheritance/Implementation:** UIListEvent extends [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md)

**Since:** 19

<!--Device-unnamed-declare interface UIListEvent extends UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIListEvent extends UIScrollableCommonEvent-End-->

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

<!--Device-UIListEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIListEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md) &#124; undefined | Yes | Callback for the **onDidScroll** event. |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnListScrollIndexCallback | undefined): void
```

Sets the callback of the [onScrollIndex](arkts-arkui-list-comp-attribute.md#onscrollindex) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIListEvent-setOnScrollIndex(callback: OnListScrollIndexCallback | undefined): void--><!--Device-UIListEvent-setOnScrollIndex(callback: OnListScrollIndexCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnListScrollIndexCallback](arkts-arkui-list-comp-onlistscrollindexcallback-t.md) &#124; undefined | Yes | Callback for the **onScrollIndex** event. |

## setOnScrollVisibleContentChange

```TypeScript
setOnScrollVisibleContentChange(callback: OnScrollVisibleContentChangeCallback | undefined): void
```

Sets the callback of the [onScrollVisibleContentChange](arkts-arkui-list-comp-attribute.md#onscrollvisiblecontentchange) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIListEvent-setOnScrollVisibleContentChange(callback: OnScrollVisibleContentChangeCallback | undefined): void--><!--Device-UIListEvent-setOnScrollVisibleContentChange(callback: OnScrollVisibleContentChangeCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnScrollVisibleContentChangeCallback](arkts-arkui-list-comp-onscrollvisiblecontentchangecallback-t.md) &#124; undefined | Yes | Callback for the **onScrollVisibleContentChange** event. |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

Sets the callback for the [onWillScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIListEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIListEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](arkts-arkui-common-comp-onwillscrollcallback-t.md) &#124; undefined | Yes | Callback for the **onWillScroll** event. |
