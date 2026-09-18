# createImageSource

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource
```

Creates an ImageSource instance based on a given URI.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-sendableimage-pixelmap-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

从API version 10开始支持SVG标签，使用版本为(SVG) 1.1, SVG标签需设置width和height。SVG文件可添加XML声明，应以**&lt;?xml**开头，当前支持的标签列表有：

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

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Image path. Currently, only the application sandbox path is supported.<br>The following formats are supported: .jpg,png,gif,bmp,webp,dng SVG, and ico. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function CreateImageSource(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
}
```

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(file.fd);
}
```

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(buf);
}
```


## createImageSource

```TypeScript
function createImageSource(fd: number): ImageSource
```

Creates an ImageSource instance based on a given file descriptor.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-sendableimage-pixelmap-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

See [createImageSource](#createimagesource)


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource
```

Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md).

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-sendableimage-pixelmap-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Array of image buffers. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

See [createImageSource](#createimagesource)
