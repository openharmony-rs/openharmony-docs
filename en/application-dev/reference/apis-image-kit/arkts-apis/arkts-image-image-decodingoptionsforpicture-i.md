# DecodingOptionsForPicture

Describes the image decoding options.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## desiredAuxiliaryPictures

```TypeScript
desiredAuxiliaryPictures: Array<AuxiliaryPictureType>
```

Auxiliary picture type. If no auxiliary picture type is specified or an empty array is passed, the system decodes all available auxiliary picture types.

To exclude all auxiliary picture, you can decode the auxiliary picture to a PixelMap and use the PixelMap to create a Picture that contains only the main picture.

**Type:** Array&lt;[AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md)&gt;

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

Desired Pixel format, RGBA_8888\BGRA_8888\RGB_565\NV12\NV21 are supported.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredSizeForMainPixelMap

```TypeScript
desiredSizeForMainPixelMap?: Size
```

Desired size of the main pixel map. The value (0, 0) indicates that the pixels are decoded based on the original image size.

**Type:** Size

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageSource
