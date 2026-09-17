# ImageErrorCallback

```TypeScript
type ImageErrorCallback = (error: ImageError) => void
```

Triggered when an error occurs during image loading.

This event is not triggered if the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [ImageError](arkts-arkui-imageerror-i.md) | Yes | Object returned by the callback triggered when an exception occurs during image loading. |
