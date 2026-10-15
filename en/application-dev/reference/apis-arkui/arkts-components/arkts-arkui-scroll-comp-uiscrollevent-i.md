# UIScrollEvent

```TypeScript
declare interface UIScrollEvent extends UIScrollableCommonEvent
```

Represents the return value of the [getEvent('Scroll')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent1) method in **frameNode**, which can be used to set scroll events for a **Scroll** node.

**UIScrollEvent** inherits from [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md).

**Inheritance/Implementation:** UIScrollEvent extends [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md)

**Since:** 19

<!--Device-unnamed-declare interface UIScrollEvent extends UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIScrollEvent extends UIScrollableCommonEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void
```

Triggered for the [onDidScroll](arkts-arkui-scroll-comp-attribute.md#ondidscroll) event.

Passing **undefined** as the input parameter resets the event callback.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollEvent-setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void--><!--Device-UIScrollEvent-setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ScrollOnScrollCallback](arkts-arkui-scroll-comp-scrollonscrollcallback-t.md) &#124; undefined | Yes | Callback for the **onDidScroll** event. |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void
```

Triggered for the [onWillScroll](arkts-arkui-scroll-comp-attribute.md#onwillscroll) event.

Passing **undefined** as the input parameter resets the event callback.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollEvent-setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void--><!--Device-UIScrollEvent-setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ScrollOnWillScrollCallback](arkts-arkui-scroll-comp-scrollonwillscrollcallback-t.md) &#124; undefined | Yes | Callback for the **onWillScroll** event. |
