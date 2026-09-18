# ContentWillScrollCallback

```TypeScript
declare type ContentWillScrollCallback = (result: SwiperContentWillScrollResult) => boolean
```

Defines the callback triggered when the **Swiper** component is about to scroll. The return value indicates whether the scroll action is allowed.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [SwiperContentWillScrollResult](arkts-arkui-swipercontentwillscrollresult-i.md) | Yes | Information related to the upcoming scroll action, including the index of the current page, the index of the page that will be displayed in the scroll direction, and the displacement of the scroll action. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the scroll action is allowed. The value **true** means the scroll action is allowed, and **false** means the opposite. |
