# AuxiliaryPictureType

Enumerates the auxiliary pictures types.

Auxiliary pictures do not directly participate in image display, and not all images contain auxiliary pictures.

Before obtaining and using a specific auxiliary picture, call [getAuxiliaryPicture](arkts-image-image-picture-i.md#getauxiliarypicture) in Picture to obtain the auxiliary picture.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## GAINMAP

```TypeScript
GAINMAP = 1
```

Gain map.

It is used to generate HDR images more accurately.

HDR synthesis usually involves using the SDR main image, gain map, and [HDR metadata](arkts-image-image-pixelmap-i.md#getmetadata) to calculate the luminance mapping.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## DEPTH_MAP

```TypeScript
DEPTH_MAP = 2
```

Depth map.

It is used to store the distance between each pixel and the camera, and provides the 3D structure of the scene.

It is useful for tasks like 3D reconstruction, background separation, and scene understanding.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## UNREFOCUS_MAP

```TypeScript
UNREFOCUS_MAP = 3
```

Unrefocus map.

It is used to store the pixel content that is not refocused during capture.

It is useful for post-processing effects such as portrait blurring, allowing users to select focus areas freely.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## LINEAR_MAP

```TypeScript
LINEAR_MAP = 4
```

Linear map.

It records lighting, color, or other visual elements linearly, providing additional data for image processing.

It is useful for visual effect enhancement and color post-processing.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## FRAGMENT_MAP

```TypeScript
FRAGMENT_MAP = 5
```

Fragment map.

It records areas of the original image obscured by watermarks. These areas might be cropped from the original image or filled with placeholder pixel data.

It is useful for watermark removal and original image restoration.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## LHDR_GAINMAP

```TypeScript
LHDR_GAINMAP = 10
```

LHDR gain map.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core
