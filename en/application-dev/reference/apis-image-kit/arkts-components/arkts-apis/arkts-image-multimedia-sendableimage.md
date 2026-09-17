# @ohos.multimedia.sendableImage

The module provides APIs for image processing based on the [Sendable](../../../arkts-utils/arkts-sendable.md) object. You can use the APIs to create a PixelMap object with specified properties or read pixels of an image (or even in a region of an image).

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [convertFromPixelMap](arkts-image-sendableimage-convertfrompixelmap-f.md) | Creates a sendable image PixelMap from image PixelMap. |
| [convertToPixelMap](arkts-image-sendableimage-converttopixelmap-f.md) | Creates a image PixelMap from sendable image PixelMap. |
| [createImageReceiver](arkts-image-sendableimage-createimagereceiver-f.md) | Creates an ImageReceiver instance based on the specified image size, format, and capacity. |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md) | Creates an ImageSource instance based on a given URI. |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md) | Creates an ImageSource instance based on a given file descriptor. |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md) | Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md). |
| [createPixelMap](arkts-image-sendableimage-createpixelmap-f.md) | Create PixelMap by data buffer. |
| [createPixelMapFromParcel](arkts-image-sendableimage-createpixelmapfromparcel-f.md) | Creates a PixelMap object based on MessageSequence parameter. |
| [createPixelMapFromSurface](arkts-image-sendableimage-createpixelmapfromsurface-f.md) | Creates a PixelMap object from surface id. |
| [createPixelMapSync](arkts-image-sendableimage-createpixelmapsync-f.md) | Create PixelMap by data buffer. |

### Interfaces

| Name | Description |
| --- | --- |
| [Image](arkts-image-sendableimage-image-i.md) | Provides APIs for basic image operations, including obtaining image information and reading and writing image data. |
| [ImageReceiver](arkts-image-sendableimage-imagereceiver-i.md) | Image receiver class. You can use it to obtain the surface ID of a component, read the latest image and the next image, and release **ImageReceiver** instances. |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | Provides APIs to obtain image information. Before calling any API in ImageSource, you must use [sendableImage.createImageSource](arkts-image-sendableimage-createimagesource-f.md) to create an ImageSource instance. |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | Sendable PixelMap instance. |
| [Region](arkts-image-sendableimage-region-i.md) | Describes the region information. It inherits from [lang.ISendable](../../../arkts-utils/arkts-sendable.md#isendable). |
| [Size](arkts-image-sendableimage-size-i.md) | Describes the size of an image. It inherits from [lang.ISendable](../../../arkts-utils/arkts-sendable.md#isendable). |

### Types

| Name | Description |
| --- | --- |
| [ISendable](arkts-image-sendableimage-isendable-t.md) | ISendable is the parent type of all sendable types except null and undefined. It does not have any necessary methods or properties. |
