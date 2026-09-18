# ImageAnimator

The **ImageAnimator** component enables images to be played a frame-by-frame basis. The list of images to be played as well as the duration of each image can be configured.

> **NOTE**

## Child Components

Not supported

## ImageAnimator

```TypeScript
ImageAnimator()
```

ImageAnimator is returned.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ImageFrameInfo](arkts-arkui-imageframeinfo-i.md) | Image frame information set. |

## Examples

```TypeScript
### Example 1: Playing an Animation Using Images of the Resource Type

This example demonstrates how to play an animation using the ImageAnimator component with images of the Resource type.


```

```TypeScript
### Example 2: Playing an Animation Using Images of the PixelMap Type

This example shows how to use the ImageAnimator component to play the PixelMap animation


```

```TypeScript
### Example 3: Enabling Automatic Pause on Invisibility

This example demonstrates how to use [monitorInvisibleArea](arkts-arkui-imageanimator-comp-attribute.md#monitorinvisiblearea) to automatically pause the ImageAnimator component when it becomes invisible and resume playback when it becomes visible again. This behavior is controlled based on the component's [state](#state) being set to AnimationStatus.Running.
```
