# createPixelMapUsingAllocator

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapUsingAllocator

```TypeScript
function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions,
    allocatorType?: AllocatorType): Promise<PixelMap>
```

Create pixelmap by data buffer based on opts, the memory type used by the PixelMap can be specified by allocatorType. By default, the system selects the memory type based on the image type, image size,platform capability, etc. When processing the PixelMap returned by this interface, please always consider the impact of stride.

**起始版本：** 20

<!--Device-image-function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions,    allocatorType?: AllocatorType): Promise<PixelMap>--><!--Device-image-function createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions,    allocatorType?: AllocatorType): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | ArrayBuffer | 是 | The image color buffer. |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | Initialization options for pixelmap. |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | Indicate which memory type will be used by the returned PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | A Promise instance used to return the PixelMap object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Memory copy failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapUsingAllocator() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // 缓冲区中的源像素数据的像素格式。
    pixelFormat: image.PixelMapFormat.BGRA_8888, // 新创建的PixelMap的像素格式。
    editable: true
  };
  image.createPixelMapUsingAllocator(color, opts, image.AllocatorType.DMA).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}

```

