# createPixelMapFromPixelsSync

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapFromPixelsSync

```TypeScript
function createPixelMapFromPixelsSync(pixels: ArrayBuffer, param: InitializationOptions): PixelMap
```

Creates a PixelMap from existing pixel data. The pixel data will be copied and converted to the specified pixel format to initialize the PixelMap.

The following pixel formats are not supported for PixelMap creation:RGBA_1010102, YCBCR_P010, YCRCB_P010, ASTC_4x4.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createPixelMapFromPixelsSync(pixels: ArrayBuffer, param: InitializationOptions): PixelMap--><!--Device-image-function createPixelMapFromPixelsSync(pixels: ArrayBuffer, param: InitializationOptions): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixels | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | The pixel data buffer used to initialize the PixelMap.The format of the pixel data can be specified by InitializationOptions.srcPixelFormat.The size of the buffer should be: image width * image height * bytes per pixel. |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | Initialization options for the PixelMap.If InitializationOptions.pixelFormat is set to ASTC_4x4, it will be reset to the default value RGBA_8888.If InitializationOptions.srcPixelFormat is set to ASTC_4x4, it will be reset to the default value BGRA_8888. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | The new PixelMap created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter.Possible cause: Size of the pixel data buffer does not match InitializationOptions.size. |
| [7600207](../errorcode-image.md#7600207-不支持的数据格式) | Unsupported pixel format. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Failed to allocate memory.Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| [7600305](../errorcode-image.md#7600305-创建pixelmap失败) | Failed to create the PixelMap.Possible causes:1. Failed to perform pixel format conversion.2. Internal data is corrupted. Please check the logs for detailed information. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromPixelsSync() {
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

  try {
    const pixelMap = image.createPixelMapFromPixelsSync(pixels, config);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}

```

