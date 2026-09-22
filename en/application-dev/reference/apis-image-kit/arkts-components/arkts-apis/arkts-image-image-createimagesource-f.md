# createImageSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource
```

Creates an ImageSource instance based on a given URI.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

The SVG tags are supported since API version 10. The used version is (SVG) 1.1, and the width and height of the SVG tag must be set. An XML declaration can be added to an SVG file and start with **&lt;?xml**. The following tags are supported:

- a  
- circle  
- clipPath  
- defs  
- ellipse  
- feBlend  
- feColorMatrix  
- feComposite  
- feDiffuseLighting  
- feDisplacementMap  
- feDistantLight  
- feFlood  
- feGaussianBlur  
- feImage  
- feMorphology  
- feOffset  
- fePointLight  
- feSpecularLighting  
- feSpotLight  
- feTurbulence  
- filter  
- g  
- image  
- line  
- linearGradient  
- mask  
- path  
- pattern  
- polygon  
- polyline  
- radialGradient  
- rect  
- stop  
- svg  
- text  
- textPath  
- tspan  
- use

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Image path. Currently, only the application sandbox path is supported.<br>The following formats are supported: .jpg,png,gif,bmp,webp,dng,heic&lt;sup&gt;12+&lt;/sup&gt; (depending on the hardware),svg&lt;sup&gt;10+&lt;/sup&gt;, and .ico&lt;sup&gt;11+&lt;/sup&gt;. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
async function CreateImageSource(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const path: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(path);
}
```


<a id="createimagesource-2"></a>

## createImageSource

```TypeScript
function createImageSource(uri: string, options: SourceOptions): ImageSource
```

Creates an ImageSource instance based on a given URI.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

The SVG tags are supported since API version 10. The used version is (SVG) 1.1, and the width and height of the SVG tag must be set. An XML declaration can be added to an SVG file and start with **&lt;?xml**. The following tags are supported:

- a  
- circle  
- clipPath  
- defs  
- ellipse  
- feBlend  
- feColorMatrix  
- feComposite  
- feDiffuseLighting  
- feDisplacementMap  
- feDistantLight  
- feFlood  
- feGaussianBlur  
- feImage  
- feMorphology  
- feOffset  
- fePointLight  
- feSpecularLighting  
- feSpotLight  
- feTurbulence  
- filter  
- g  
- image  
- line  
- linearGradient  
- mask  
- path  
- pattern  
- polygon  
- polyline  
- radialGradient  
- rect  
- stop  
- svg  
- text  
- textPath  
- tspan  
- use

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Image path. Currently, only the application sandbox path is supported.<br>The following formats are supported: .jpg,png,gif,bmp,webp,dng,heic&lt;sup&gt;12+&lt;/sup&gt; (depending on the hardware),svg&lt;sup&gt;10+&lt;/sup&gt; and .ico&lt;sup&gt;11+&lt;/sup&gt;. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | Yes | Image properties, including the image pixel density, pixel format, and image size. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 'test.png' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const path: string = context.filesDir + "/test.png";
  let imageSourceObj: image.ImageSource = image.createImageSource(path, sourceOptions);
}
```


<a id="createimagesource-4"></a>

## createImageSource

```TypeScript
function createImageSource(fd: number): ImageSource
```

Creates an ImageSource instance based on a given file descriptor.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  let filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd);
}
```


<a id="createimagesource-6"></a>

## createImageSource

```TypeScript
function createImageSource(fd: number, options: SourceOptions): ImageSource
```

Creates an ImageSource instance based on a given file descriptor.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | Yes | Image properties, including the image pixel density, pixel format, and image size. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd, sourceOptions);
}
```


<a id="createimagesource-8"></a>

## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource
```

Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [image.createPixelMapSync](arkts-image-image-imagesource-i.md#createpixelmapsync). Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Array of image buffers. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  const imageSourceObj: image.ImageSource = image.createImageSource(buf);
}
```


<a id="createimagesource-10"></a>

## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource
```

Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [image.createPixelMapSync](arkts-image-image-imagesource-i.md#createpixelmapsync). Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Array of image buffers. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | Yes | Image properties, including the image pixel density, pixel format, and image size. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
async function CreateImageSource() {
  const data: ArrayBuffer = new ArrayBuffer(112);
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  const imageSourceObj: image.ImageSource = image.createImageSource(data, sourceOptions);
}
```


<a id="createimagesource-12"></a>

## createImageSource

```TypeScript
function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource
```

Creates an ImageSource instance based on the raw file descriptor of an image resource file. Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rawfile | [resourceManager.RawFileDescriptor](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-rawfiledescriptor-t.md) | Yes | Raw file descriptor of the image resource file. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | No | Image properties, including the image pixel density, pixel format, and image size. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';
  
async function CreateImageSource(context : Context) {
  // Obtain a resource manager.
  const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  resourceMgr.getRawFd('test.jpg').then((rawFileDescriptor: resourceManager.RawFileDescriptor) => {
    const imageSourceObj: image.ImageSource = image.createImageSource(rawFileDescriptor);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get RawFileDescriptor.code is ${error.code}, message is ${error.message}`);
  })
}
```
