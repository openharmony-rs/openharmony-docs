# CropAndScaleStrategy

Enumerates the order of cropping and scaling.

If the **cropAndScaleStrategy** parameter is not specified in [DecodingOptions](arkts-image-image-decodingoptions-i.md) and both **desiredRegion** and **desiredSize** are set, the final decoding result may vary slightly due to differences in decoding algorithms used for different image formats.

For example, if the original image size is 200x200, and you specify **desiredSize:{width: 150, height: 150}, desiredRegion:{x: 0, y: 0, width: 100, height: 100}**, the expectation is to decode the top-left 1/4 region of the original image and then scale the pixelMap size to 150x150.

For JPEG and WebP images (as well as some DNG images that decode a JPEG preview within the file and therefore are treated as JPEG format), the system first performs downsampling. For instance, it might downsample by 7/8 and then crop the region based on a 175x175 image size. As a result, the final cropped region will be slightly larger than the top-left 1/4 of the original image.

For SVG images, which are vector-based and can be scaled without losing clarity, the system scales the image based on the ratio of **desiredSize** to the original image size and then crops the region. This results in a decoded region that may differ from the exact 1/4 region of the original image.

To ensure consistent results when both **desiredRegion** and **desiredSize** are set, set the **cropAndScaleStrategy** parameter to **CROP_FIRST**.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

## SCALE_FIRST

```TypeScript
SCALE_FIRST = 1
```

If both **desiredRegion** and **desiredSize** are specified, the image is first scaled based on **desiredSize** and then cropped based on **desiredRegion**.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

## CROP_FIRST

```TypeScript
CROP_FIRST = 2
```

If both **desiredRegion** and **desiredSize** are specified, the image is first cropped based on **desiredRegion** and then scaled based on **desiredSize**.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core
