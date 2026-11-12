# CursorContextChangeCallback

```TypeScript
export type CursorContextChangeCallback = (x: number, y: number, height: number) => void
```

The callback of 'cursorContextChange' event.

**Since:** 26.1.0

<!--Device-inputMethodEngine-export type CursorContextChangeCallback = (x: double, y: double, height: double) => void--><!--Device-inputMethodEngine-export type CursorContextChangeCallback = (x: double, y: double, height: double) => void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the left point of the cursor, unit is px. |
| y | number | Yes | the top point of the cursor, unit is px. |
| height | number | Yes | the height of the cursor, unit is px. |
