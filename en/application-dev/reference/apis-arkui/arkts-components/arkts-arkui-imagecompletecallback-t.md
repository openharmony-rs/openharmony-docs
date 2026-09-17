# ImageCompleteCallback

```TypeScript
type ImageCompleteCallback = (result: ImageLoadResult) => void
```

Defines the callback triggered when the image is successfully loaded or decoded.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [ImageLoadResult](arkts-arkui-imageloadresult-i.md) | Yes | Object returned after the callback is triggered when an image is successfully loaded or decoded. |
