# @ohos.arkui.drawableDescriptor(DrawableDescriptor)

This module provides capabilities for layered icon composition (foreground, background, mask), animated image
 control, and basic image processing.

> **NOTE**
 >
 > - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.



## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AnimatedDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) | Defines a descriptor object used to play animated content (for example, **PixelMap** arrays or animated image resources) using the Image component. It inherits from [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md). |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | Represents the base class providing overridable methods for [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) acquisition and image resource loading. |
| [LayeredDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md) | Creates a **LayeredDrawableDescriptor** object when the passed resource ID or name belongs to a JSON file that contains foreground and background resources. Inherits from [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md). |
| [PictureDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-picturedrawabledescriptor-c.md) | Creates a **PictureDrawableDescriptor** object by passing a **Picture** object. This API inherits from [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md). |
| [PixelMapDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-pixelmapdrawabledescriptor-c.md) | Implements a **PixelMapDrawableDescriptor** object, which can be created by passing in a **PixelMap** object. Inherits from [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md). |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c-sys.md) | Represents the base class providing overridable methods for [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) acquisition and image resource loading. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AnimationController](arkts-arkui-arkui-drawabledescriptor-animationcontroller-i.md) | Implements an animation controller object. It provides APIs for playing, stopping, resuming, and pausing animations, as well as querying the status. |
| [AnimationOptions](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | Provides the configuration options for animation playback, including the playback duration, number of playback times, and autoplay behavior. |
| [DrawableDescriptorLoadedResult](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md) | Represents the result of loading an image resource or URI. |
| [HdrCompositionConfig](arkts-arkui-arkui-drawabledescriptor-hdrcompositionconfig-i.md) | Provides HDR composition configuration. |

### Enums

| Name | Description |
| --- | --- |
| [AnimationStopMode](arkts-arkui-arkui-drawabledescriptor-animationstopmode-e.md) | Enumerates the stop modes of an animation. |
