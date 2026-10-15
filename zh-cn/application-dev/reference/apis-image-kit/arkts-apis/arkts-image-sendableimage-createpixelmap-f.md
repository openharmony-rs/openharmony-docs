# createPixelMap

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMap

```TypeScript
function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>
```

通过像素数据和图像属性创建PixelMap。传入的像素数据会进行拷贝并转换为[InitializationOptions](arkts-image-image-initializationoptions-i.md).pixelFormat指定的像素格式，用于初始化PixelMap的像素。使用Promise异步回调。

> **说明：** 
> 
> - 此接口不支持创建以下像素格式的PixelMap：RGBA_1010102、YCBCR_P010、YCRCB_P010和ASTC_4x4。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

<!--Device-sendableImage-function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>--><!--Device-sendableImage-function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | ArrayBuffer | 是 | 图像像素数据的缓冲区，用于初始化PixelMap的像素。缓冲区内的像素数据必须紧密排列，不可以包含内存对齐填充字节。<br>缓冲区的像素格式需要由[InitializationOptions](arkts-image-image-initializationoptions-i.md).srcPixelFormat指定，否则默认缓冲区的像素格式为BGRA_8888。<br>**说明：** 缓冲区长度为：图像宽度 * 图像高度 * 每像素字节数。 |
| options | [image.InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | 创建图像的初始化属性，包括尺寸、像素格式、透明度类型、缩放模式和是否可编辑。<br>**说明：** 如果像素格式被指定为ASTC_4x4，则会使用默认的RGBA_8888格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-sendableimage-pixelmap-i.md)&gt; | Promise对象，返回创建的PixelMap。<br>当创建的PixelMap大小超过源像素数据所能表示的图像大小时，返回按源像素数据所能表示的图像大小创建的PixelMap。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // 缓冲区中的源像素数据的像素格式。
    pixelFormat: image.PixelMapFormat.BGRA_8888, // 新创建的PixelMap的像素格式。
    editable: true
  };
  sendableImage.createPixelMap(color, opts).then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```
