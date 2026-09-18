# cancelAnimationFrame

## cancelAnimationFrame

```TypeScript
export declare function cancelAnimationFrame(requestId: number): void
```

Cancels the vsync callback set by "requestAnimationFrame()".

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestId | number | Yes | Indicates the vsync callback ID returned by "requestAnimationFrame()". |
