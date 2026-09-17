# SegmentButtonItemArray

```TypeScript
declare type SegmentButtonItemArray = Array<SegmentButtonTextItem> | Array<SegmentButtonIconItem> | Array<SegmentButtonIconTextItem>
```

Represents the array union type used to store button information.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| Array&lt;SegmentButtonTextItem&gt; | An array of text-only button information. |
| Array&lt;SegmentButtonIconItem&gt; | An array of icon-only button information. |
| Array&lt;SegmentButtonIconTextItem&gt; | An array of icon and text button information. |
