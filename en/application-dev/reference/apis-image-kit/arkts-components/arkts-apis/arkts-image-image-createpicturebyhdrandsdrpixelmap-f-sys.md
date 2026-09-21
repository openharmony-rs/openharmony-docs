# createPictureByHdrAndSdrPixelMap (System API)

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPictureByHdrAndSdrPixelMap

```TypeScript
function createPictureByHdrAndSdrPixelMap(hdrPixelMap: PixelMap, sdrPixelMap: PixelMap): Promise<Picture>
```

Creates a Picture object based on an HDR PixelMap and an SDR PixelMap. The system uses the HDR PixelMap and SDR PixelMap to generate a gainmap. The returned Picture object contains the SDR PixelMap and the generated gainmap, both in RGBA8888 format. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hdrPixelMap | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | HDR PixelMap, with 16-bit or 10-bit depth, in FP16/RGBA1010102/YCBCR_P010 format, and BT2020_HLG color space. |
| sdrPixelMap | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | SDR PixelMap, with 8-bit depth, in RGBA8888/NV21 format, and P3 color space. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md)&gt; | Picture object that contains the SDR PixelMap and gainmap, both in RGBA8888 format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation. HdrPixelMap's PixelMapFormat is not RGBA_F16\RGBA_1010102\YCBCR_P010, or its color space is not BT2020_HLG. Or sdrPixelMap's PixelMapFormat is not RGBA_8888\NV21\NV12, or its color space is not P3. |

**Examples**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg"); // SDR
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let options1: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.SDR,
  }
  let options2: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.HDR, // Decode an SDR PixelMap into an HDR PixelMap using AIHDR.
  }
  let sdrPixelMap = await imageSource.createPixelMap(options1);
  let hdrPixelMap = await imageSource.createPixelMap(options2);

  // Obtain the gainmap generated and encode the gainmap.
  let picture: image.Picture = await image.createPictureByHdrAndSdrPixelMap(hdrPixelMap, sdrPixelMap);
  if (picture != null) {
    console.info('Create picture succeeded');
  } else {
    console.error('Create picture failed');
  }
  const imagePackerObj = image.createImagePacker();
  let packOpts : image.PackingOption = { format : "image/jpeg", quality: 98};
  packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
  const path: string = context.filesDir + "/hdr-test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  imagePackerObj.packToFile(picture, file.fd, packOpts).then(() => {
  }).catch((error : BusinessError) => {
    console.error('Failed to pack the image. And the error is: ' + error);
  })
}
```


<a id="createpicturebyhdrandsdrpixelmap-1"></a>

## createPictureByHdrAndSdrPixelMap

```TypeScript
function createPictureByHdrAndSdrPixelMap(hdrPixelMap: PixelMap, sdrPixelMap: PixelMap, 
      params: GainmapParams): Promise<Picture>
```

Creates a Picture object by a HDR PixelMap and a SDR PixelMap with specified options. A gainmap will be generated using the HDR and SDR PixelMap, and the returned Picture will contain the SDR PixelMap and the generated gainmap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hdrPixelMap | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | A HDR PixelMap, whose PixelMapFormat should be RGBA_F16\RGBA_1010102\YCBCR_P010 and color space should be BT2020_HLG |
| sdrPixelMap | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | A SDR PixelMap, whose PixelMapFormat should be RGBA_8888\NV21\NV12 and color space should be P3. |
| params | [GainmapParams](arkts-image-image-gainmapparams-i-sys.md) | Yes | Gainmap generation parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md)&gt; | Returns the Picture object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation. HdrPixelMap's PixelMapFormat is not RGBA_F16\RGBA_1010102\YCBCR_P010, or its color space is not BT2020_HLG. Or sdrPixelMap's PixelMapFormat is not RGBA_8888\NV21\NV12, or its color space is not P3. |

**Examples**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function CreatePictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg"); // Obtain an SDR image.
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let decodingOptionsForSDR: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.SDR,
  }
  let decodingOptionsForHDR: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.HDR, // Decode an SDR PixelMap into an HDR PixelMap using AIHDR.
  }
  let sdrPixelMap = await imageSource.createPixelMap(decodingOptionsForSDR);
  let hdrPixelMap = await imageSource.createPixelMap(decodingOptionsForHDR);
  let params : image.GainmapParams = {
    isFullSizeGainmap: true
  }

  // Obtain the gainmap generated and encode the gainmap.
  let picture: image.Picture = await image.createPictureByHdrAndSdrPixelMap(hdrPixelMap, sdrPixelMap, params);
  if (picture != null) {
    console.info('Succeeded in creating picture');
  } else {
    console.error('Create picture failed');
  }
  const imagePackerObj = image.createImagePacker();
  let packOpts : image.PackingOption = { format : "image/jpeg", quality: 98};
  packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
  const path: string = context.filesDir + "/hdr-test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  imagePackerObj.packToFile(picture, file.fd, packOpts).then(() => {
  }).catch((error : BusinessError) => {
    console.error('Failed to pack the image. And the error is: ' + error);
  })
}
```
