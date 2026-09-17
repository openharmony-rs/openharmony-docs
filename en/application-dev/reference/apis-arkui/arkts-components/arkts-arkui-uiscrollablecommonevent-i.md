# UIScrollableCommonEvent

Defines a UIScrollableCommonEvent which is used to set event to target component.

**Inheritance/Implementation:** UIScrollableCommonEvent extends [UICommonEvent](arkts-arkui-uicommonevent-i.md)

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setOnReachEnd

```TypeScript
setOnReachEnd(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling reaches the end position.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; &#124; undefined | Yes | callback function, triggered when the scrolling reaches the end position. |

## setOnReachStart

```TypeScript
setOnReachStart(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling reaches the start position.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; &#124; undefined | Yes | callback function, triggered when the scrolling reaches the start position. |

## setOnScrollFrameBegin

```TypeScript
setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void
```

Set or reset the callback which is triggered when scrolling begin each frame.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) &#124; undefined | Yes | callback function, triggered when the scrolling begin each frame. |

## setOnScrollStart

```TypeScript
setOnScrollStart(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling started.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; &#124; undefined | Yes | callback function, triggered when the scrolling started. |

## setOnScrollStop

```TypeScript
setOnScrollStop(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling stoped.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; &#124; undefined | Yes | callback function, triggered when the scrolling stoped. |
