# UIScrollableCommonEvent

```TypeScript
declare interface UIScrollableCommonEvent extends UICommonEvent
```

Configures scroll event callbacks.

**Inheritance/Implementation:** UIScrollableCommonEvent extends [UICommonEvent](arkts-arkui-common-comp-uicommonevent-i.md)

**Since:** 19

<!--Device-unnamed-declare interface UIScrollableCommonEvent extends UICommonEvent--><!--Device-unnamed-declare interface UIScrollableCommonEvent extends UICommonEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setOnReachEnd

```TypeScript
setOnReachEnd(callback: Callback<void> | undefined): void
```

Sets the callback for the [onReachEnd](arkts-arkui-common-comp-scrollablecommonmethod-c.md#onreachend) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the **onReachEnd** event. |

## setOnReachStart

```TypeScript
setOnReachStart(callback: Callback<void> | undefined): void
```

Sets the callback for the [onReachStart](arkts-arkui-common-comp-scrollablecommonmethod-c.md#onreachstart) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollableCommonEvent-setOnReachStart(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachStart(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the **onReachStart** event. |

## setOnScrollFrameBegin

```TypeScript
setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void
```

Sets the callback for the [onScrollFrameBegin](arkts-arkui-scroll-comp-attribute.md#onscrollframebegin) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnScrollFrameBeginCallback](arkts-arkui-scroll-comp-onscrollframebegincallback-t.md) &#124; undefined | Yes | Callback for the **onScrollFrameBegin** event. |

## setOnScrollStart

```TypeScript
setOnScrollStart(callback: Callback<void> | undefined): void
```

Sets the callback for the [onScrollStart](arkts-arkui-common-comp-scrollablecommonmethod-c.md#onscrollstart) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the **onScrollStart** event. |

## setOnScrollStop

```TypeScript
setOnScrollStop(callback: Callback<void> | undefined): void
```

Sets the callback for the [onScrollStop](arkts-arkui-common-comp-scrollablecommonmethod-c.md#onscrollstop) event.

If the input parameter is **undefined**, the event callback is reset.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the **onScrollStop** event. |
