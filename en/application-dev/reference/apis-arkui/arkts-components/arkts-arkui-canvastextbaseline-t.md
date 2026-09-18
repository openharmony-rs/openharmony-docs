# CanvasTextBaseline

```TypeScript
declare type CanvasTextBaseline = "alphabetic" | "bottom" | "hanging" | "ideographic" | "middle" | "top"
```

Defines the text baseline type. The value type is a union of the types listed in the table below.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| "alphabetic" | The text baseline is the normal alphabetic baseline. |
| "bottom" | The text baseline is at the bottom of the text bounding box. Its difference from the ideographic baseline is that the ideographic baseline does not consider letters in the next line. |
| "hanging" | The text baseline is a hanging baseline over the text. |
| "ideographic" | The text baseline is the ideographic baseline. If a character exceeds the alphabetic baseline, the ideographic baseline is located at the bottom of the excessive character. |
| "middle" | The text baseline is in the middle of the text bounding box. |
| "top" | The text baseline is on the top of the text bounding box. |
