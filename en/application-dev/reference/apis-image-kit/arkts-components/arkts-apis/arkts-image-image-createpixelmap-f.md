# createPixelMap

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMap

```TypeScript
function createPixelMap(colors: ArrayBuffer, options: InitializationOptions, callback: AsyncCallback<PixelMap>): void
```

Create pixelmap by data buffer.

Starting from API 26.0.0, it is recommended to use [createPixelMapFromPixels](arkts-image-image-createpixelmapfrompixels-f.md) instead for better exception handling capabilities.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | ArrayBuffer | Yes | The image color buffer. |
| options | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for pixelmap. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the PixelMap object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMap(color, opts, (err: BusinessError, pixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in creating the PixelMap.');
  });
}
```


## createPixelMap

```TypeScript
function createPixelMap(colors: ArrayBuffer, options: InitializationOptions): Promise<PixelMap>
```

Create pixelmap by data buffer.

Starting from API 26.0.0, it is recommended to use [createPixelMapFromPixels](arkts-image-image-createpixelmapfrompixels-f.md) instead for better exception handling capabilities.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | ArrayBuffer | Yes | The image color buffer. |
| options | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for pixelmap. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | A Promise instance used to return the PixelMap object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMap(color, opts, (err: BusinessError, pixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in creating the PixelMap.');
  });
}
```
