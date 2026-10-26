# createPixelMapUsingAllocatorSync

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapUsingAllocatorSync

```TypeScript
function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions,
    allocatorType?: AllocatorType): PixelMap
```

通过像素数据和图像属性创建PixelMap，可以指定内存类型。传入的像素数据会进行拷贝并转换为[InitializationOptions](arkts-image-image-initializationoptions-i.md).pixelFormat指定的像素格式，用于初始化PixelMap的像素。同步返回结果。

> **说明：** 
> 
> - 此接口不支持创建以下像素格式的PixelMap：YCBCR_P010、YCRCB_P010和ASTC_4x4。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 20

<!--Device-image-function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions,    allocatorType?: AllocatorType): PixelMap--><!--Device-image-function createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions,    allocatorType?: AllocatorType): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | ArrayBuffer | 是 | 图像像素数据的缓冲区，用于初始化PixelMap的像素。缓冲区内的像素数据必须紧密排列，不可以包含内存对齐填充字节。<br>初始化前，必须通过[InitializationOptions](arkts-image-image-initializationoptions-i.md).srcPixelFormat指定缓冲区的像素格式，否则会创建失败。<br>**说明：** 缓冲区长度为：图像宽度 * 图像高度 * 每像素字节数。 |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | 创建图像的初始化属性，包括尺寸、像素格式、透明度类型、缩放模式和是否可编辑。<br>**说明：** 如果像素格式被指定为ASTC_4x4，则会使用默认的RGBA_8888格式。 |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | 指定创建PixelMap的内存类型，默认值为AllocatorType.AUTO。<br>1. image.AllocatorType.AUTO：不支持该内存类型的格式有UNKNOWN、YCBCR_P010、YCRCB_P010和ASTC_4x4。<br>RGBA_1010102默认申请DMA内存。<br>RGB_565、RGBA_8888、BGRA_8888、RGBA_F16和ALPHA_F16（从API版本26.0.0开始支持）尺寸大于等于512*512像素时默认申请DMA内存，否则申请共享内存。<br>其余格式默认申请共享内存。<br>2. image.AllocatorType.DMA：RGBA_1010102、RGB_565、RGBA_8888、BGRA_8888、RGBA_F16和ALPHA_F16支持DMA内存类型，其余格式不支持。<br>3. image.AllocatorType.SHARE_MEMORY：UNKNOWN、RGBA_1010102、YCBCR_P010、YCRCB_P010和ASTC_4x4不支持共享内存，其余格式支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | 返回创建的PixelMap对象，接口调用失败时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |
| [7600302](../errorcode-image.md#7600302-内存拷贝失败) | Memory copy failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapUsingAllocatorSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // 缓冲区中的源像素数据的像素格式。
    pixelFormat: image.PixelMapFormat.BGRA_8888, // 新创建的PixelMap的像素格式。
    editable: true
  };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapUsingAllocatorSync(color, opts, image.AllocatorType.DMA);
    if (pixelMap == undefined) {
      console.error(`Failed to create the PixelMap.`);
      return;
    }
    console.info('Succeeded in creating the PixelMap.');
  } catch (error) {
    const err = error as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```


## createPixelMapUsingAllocatorSync

```TypeScript
function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap
```

通过图像属性创建空白PixelMap，可以指定内存类型。同步返回结果。

> **说明：** 
> 
> - 此接口不支持创建以下像素格式的PixelMap：ASTC_4x4。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 20

<!--Device-image-function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap--><!--Device-image-function createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | 创建图像的初始化属性，包括尺寸、像素格式、透明度类型、缩放模式和是否可编辑。<br>**说明：** 如果像素格式被指定为ASTC_4x4，则会使用默认的RGBA_8888格式。 |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | 指定创建PixelMap的内存类型，默认值为AllocatorType.AUTO。<br>1. image.AllocatorType.AUTO：不支持该内存类型的格式有UNKNOWN和ASTC_4x4。<br>RGBA_1010102、YCBCR_P010和YCRCB_P010默认申请DMA内存。<br>RGB_565、RGBA_8888、BGRA_8888、RGBA_F16和ALPHA_F16（从API版本26.0.0开始支持）尺寸大于等于512*512像素时默认申请DMA内存，否则申请共享内存。<br>其余格式默认申请共享内存。<br>2. image.AllocatorType.DMA：RGBA_1010102、RGB_565、RGBA_8888、BGRA_8888、RGBA_F16、ALPHA_F16、YCBCR_P010和YCRCB_P010支持DMA内存类型，其余格式不支持。<br>3. image.AllocatorType.SHARE_MEMORY：UNKNOWN、RGBA_1010102、YCBCR_P010、YCRCB_P010和ASTC_4x4不支持共享内存，其余格式支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | 返回创建的PixelMap对象，接口调用失败时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Memory alloc failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapUsingAllocatorSync() {
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.BGRA_8888, size: { height: 4, width: 6 } };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapUsingAllocatorSync(opts, image.AllocatorType.DMA);
    if (pixelMap == undefined) {
      console.error(`Failed to create the PixelMap.`);
      return;
    }
    console.info('Succeeded in creating the PixelMap.');
  } catch (error) {
    const err = error as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```
