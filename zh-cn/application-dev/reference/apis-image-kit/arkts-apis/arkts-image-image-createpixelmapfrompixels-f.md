# createPixelMapFromPixels

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapFromPixels

```TypeScript
function createPixelMapFromPixels(pixels: ArrayBuffer, param: InitializationOptions): Promise<PixelMap>
```

通过像素数据和图像属性创建PixelMap。传入的像素数据会进行拷贝并转换为[InitializationOptions](arkts-image-image-initializationoptions-i.md).pixelFormat指定的像素格式，用于初始化PixelMap的像素。使用Promise异步回调。

> **说明：** 
> 
> - 此接口不支持创建以下像素格式的PixelMap：RGBA_1010102、YCBCR_P010、YCRCB_P010和ASTC_4x4。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createPixelMapFromPixels(pixels: ArrayBuffer, param: InitializationOptions): Promise<PixelMap>--><!--Device-image-function createPixelMapFromPixels(pixels: ArrayBuffer, param: InitializationOptions): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixels | ArrayBuffer | 是 | 图像像素数据的缓冲区，用于初始化PixelMap的像素。缓冲区内的像素数据必须紧密排列，不可以包含内存对齐填充字节。<br>缓冲区的像素格式需要由[InitializationOptions](arkts-image-image-initializationoptions-i.md).srcPixelFormat指定，否则默认缓冲区的像素格式为BGRA_8888。<br>**说明：** 缓冲区长度为：图像宽度 * 图像高度 * 每像素字节数。 |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | 创建图像的初始化属性，包括尺寸、像素格式、透明度类型、缩放模式和是否可编辑。<br>**说明：** 如果像素格式被指定为ASTC_4x4，则会使用默认的RGBA_8888格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise对象，返回创建的PixelMap对象，接口调用失败时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: Size of the pixel data buffer does not match InitializationOptions.size. |
| [7600207](../errorcode-image.md#7600207-不支持的数据格式) | Unsupported pixel format. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap. Possible causes: 1. Failed to perform pixel format conversion. 2. Internal data is corrupted. Please check the logs for detailed information. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromPixels() {
  const size: image.Size = {
    width: 6,
    height: 4
  };
  const pixels = new ArrayBuffer(size.width * size.height * 4); // 4为RGBA类型像素格式的每像素字节数。
  const pixelsArr = new Uint8Array(pixels);
  for (let i = 0; i < pixelsArr.length; i += 4) {
    // RGBA_8888格式下，下列数组索引依次为：R通道、G通道、B通道、A通道。
    pixelsArr[i] = 0xFF;
    pixelsArr[i + 1] = 0x00;
    pixelsArr[i + 2] = 0x00;
    pixelsArr[i + 3] = 0xFF;
  }
  const config: image.InitializationOptions = {
    size,
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // 缓冲区内的源像素数据的像素格式。
    pixelFormat: image.PixelMapFormat.BGRA_8888, // 新创建的PixelMap的像素格式。
    editable: true
  };

  image.createPixelMapFromPixels(pixels, config)
    .then((pixelMap: image.PixelMap) => {
      console.info('Succeeded in creating the PixelMap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```
