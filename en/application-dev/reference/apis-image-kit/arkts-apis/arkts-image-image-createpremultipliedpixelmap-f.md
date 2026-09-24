# createPremultipliedPixelMap

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPremultipliedPixelMap

```TypeScript
function createPremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void
```

Transforms pixelmap from unpremultiplied alpha format to premultiplied alpha format.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The source pixelmap. |
| dst | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The destination pixelmap. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980103](../errorcode-image.md#62980103-unsupported-image-type) | The image data is not supported. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980246](../errorcode-image.md#62980246-failure-in-reading-the-pixelmap) | Failed to read the pixelMap. |
| [62980248](../errorcode-image.md#62980248-no-modification-to-the-pixelmap) | Pixelmap not allow modify. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i + 1] = 255;
    bufferArr[i + 2] = 122;
    bufferArr[i + 3] = 122;
  }
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.UNPREMUL};
  let srcPixelMap = image.createPixelMapSync(color, optsForUnpre);
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.PREMUL};
  let dstPixelMap = image.createPixelMapSync(optsForPre);
  image.createPremultipliedPixelMap(srcPixelMap, dstPixelMap, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in converting the PixelMap.');
  });
}
```


<a id="createpremultipliedpixelmap-1"></a>

## createPremultipliedPixelMap

```TypeScript
function createPremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>
```

Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The source pixelMap. |
| dst | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The destination pixelmap. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980103](../errorcode-image.md#62980103-unsupported-image-type) | The image data is not supported. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980246](../errorcode-image.md#62980246-failure-in-reading-the-pixelmap) | Failed to read the pixelMap. |
| [62980248](../errorcode-image.md#62980248-no-modification-to-the-pixelmap) | Pixelmap not allow modify. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i + 1] = 255;
    bufferArr[i + 2] = 122;
    bufferArr[i + 3] = 122;
  }
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.UNPREMUL};
  let srcPixelMap = image.createPixelMapSync(color, optsForUnpre);
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.PREMUL};
  let dstPixelMap = image.createPixelMapSync(optsForPre);
  image.createPremultipliedPixelMap(srcPixelMap, dstPixelMap).then(() => {
    console.info('Succeeded in converting the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```
