# Image Region Decoding and Downsampling (ArkTS)

<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T07:06:02.682Z pushedAt=2026-06-03T10:13:31.956Z -->

When processing large images, decoding the entire image directly may lead to high memory usage and long decoding time. Region decoding and downsampling decoding can effectively optimize this scenario:

- **Region Decoding**: Decodes only the specified rectangular region of an image, suitable for scenarios where you need to view a partial area of the image.

- **Downsampling Decoding**: Decodes the image to the desired size, with the decoder automatically selecting the optimal sampling rate, suitable for large image preview scenarios.

**Applicable Scenarios**:

| Scenario | Recommended Approach | Description |
|------|----------|------|
| Partial zoom-in viewing of an image | Region decoding | Decodes only the region to be viewed. |
| Large image preview (e.g., displaying a 4K image on a phone screen) | Downsampling decoding | Reduces resolution to lower memory usage. |
| Map/panorama tile loading | Combined use | Specifies a region and an output size. |

## Region Decoding

Region decoding specifies the rectangular region to be decoded by setting the decoding parameter desiredRegion. The decoder only decodes data within that region. For details about the parameter, see [Region](../../reference/apis-image-kit/arkts-apis-image-i.md#region8).

### How to Develop

1. Create an ImageSource instance by referring to [Using ImageSource to Decode Images](image-decoding.md).

2. Set the desiredRegion parameter to perform region decoding.

   <!-- @[decode_region](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) --> 

   ``` TypeScript
   async DecodeRegion(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
     let decodingOptions: image.DecodingOptions = {
       desiredRegion: {
         size: { width: 1000, height: 1000 },
         x: 0,
         y: 0
       }
     };
   
     try {
       let pixelMap = await imageSource.createPixelMap(decodingOptions);
       console.info('Succeeded in decoding region.');
       return pixelMap;
     } catch (error) {
       console.error(`Failed to decode region: ${error}.`);
       return undefined;
     }
   }
   ```

### Limitations

- The region coordinates and size must be within the original image bounds.

- The region size must be a positive integer.

## Downsampling Decoding

Downsampling decoding specifies the desired output image size by setting the decoding parameter desiredSize. The decoder outputs a PixelMap based on the desired size, reducing the final memory usage.

**Decoding processing differences**:

- **JPEG, PNG, and HEIF formats**: A downsampling strategy is used during decoding, with decoding performed at the optimal sampling rate for higher decoding efficiency.

- **Other formats**: The original image is fully decoded first, and then scaled to the desired size.

For details about the parameters, see [DecodingOptions](../../reference/apis-image-kit/arkts-apis-image-i.md#decodingoptions7).

### How to Develop

1. Create an ImageSource instance by referring to [Using ImageSource for Image Decoding](image-decoding.md).

2. Set the desiredSize parameter to perform downsampling decoding.

   <!-- @[decode_downsample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) --> 

   ``` TypeScript
   async DownsampleDecode(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
     let decodingOptions: image.DecodingOptions = {
       desiredSize: { width: 512, height: 512 }
     };
   
     try {
       let pixelMap = await imageSource.createPixelMap(decodingOptions);
       console.info('Succeeded in downsample decoding.');
       return pixelMap;
     } catch (error) {
       console.error(`Failed to downsample decode: ${error}.`);
       return undefined;
     }
   }
   ```

## Combining Region Decoding and Downsampling

When both desiredRegion and desiredSize are set, use the cropAndScaleStrategy parameter to specify the order of cropping and scaling.

### cropAndScaleStrategy Policy

| Policy | Constant Value | Operation Order | Description |
|------|--------|----------|------|
| SCALE_FIRST | 1 | Scale first, then crop. | - |
| CROP_FIRST | 2 | Crop first, then scale. | Recommended, reduces peak decoding memory. |

**CROP_FIRST is recommended**: Cropping first and then scaling allows precise control over the crop region, ensuring consistent decoding results across different formats.

For details about the parameters, see [CropAndScaleStrategy](../../reference/apis-image-kit/arkts-apis-image-e.md#cropandscalestrategy18).

### How to Develop

1. Create an ImageSource instance by referring to [Using ImageSource to Decode Images](image-decoding.md).

2. Set the desiredRegion, desiredSize, and cropAndScaleStrategy parameters simultaneously.

   <!-- @[decode_combined](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/CodecUtility.ets) --> 

   ``` TypeScript
   async CombinedDecode(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
     let decodingOptions: image.DecodingOptions = {
       desiredRegion: {
         size: { width: 2000, height: 2000 },
         x: 1000,
         y: 500
       },
       desiredSize: { width: 512, height: 512 },
       cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST
     };
   
     try {
       let pixelMap = await imageSource.createPixelMap(decodingOptions);
       console.info('Succeeded in combined decoding.');
       return pixelMap;
     } catch (error) {
       console.error(`Failed to combined decode: ${error}.`);
       return undefined;
     }
   }
   ```

## Notes

- When setting both desiredRegion and desiredSize, it is recommended to set cropAndScaleStrategy to CROP_FIRST to ensure consistent decoding results.

- For images whose original pixel memory exceeds 2 GB, it is recommended to use downsampling decoding to avoid memory overflow.