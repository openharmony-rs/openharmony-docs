# createAuxiliaryPictureUsingAllocator

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createAuxiliaryPictureUsingAllocator

```TypeScript
function createAuxiliaryPictureUsingAllocator(auxiliaryPictureInfo: AuxiliaryPictureInfo,
    allocatorType?: AllocatorType, pixels?: ArrayBuffer): AuxiliaryPicture
```

使用指定的内存类型，根据辅助图信息和像素数据创建辅助图对象。

> **说明：**  
>  
> - 在处理此接口返回的AuxiliaryPicture时，需要考虑内存中每行像素所占的空间的影响。  
>  
> - 创建的辅助图像会使用输入的像素进行初始化。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-image-function createAuxiliaryPictureUsingAllocator(auxiliaryPictureInfo: AuxiliaryPictureInfo,
    allocatorType?: AllocatorType, pixels?: ArrayBuffer): AuxiliaryPicture--><!--Device-image-function createAuxiliaryPictureUsingAllocator(auxiliaryPictureInfo: AuxiliaryPictureInfo,
    allocatorType?: AllocatorType, pixels?: ArrayBuffer): AuxiliaryPicture-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| auxiliaryPictureInfo | [AuxiliaryPictureInfo](arkts-image-image-auxiliarypictureinfo-i.md) | 是 | 辅助图图像信息。<br>- 输入的ArrayBuffer的pixelFormat和最终创建出的辅助图的实际pixelFormat需与auxiliaryPictureInfo中指定的pixelFormat保持一致。<br>- 当AuxiliaryPictureType为GAINMAP时，AllocatorType仅支持传入AUTO/DMA。<br>- 当传入SHARE_MEMORY时，返回错误码7600205。 |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | 否 | 图像解码的内存类型，AUTO及默认情况下按照DMA处理。 |
| pixels | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 否 | 以buffer形式存放的图像数据。<br>当未提供ArrayBuffer参数时，默认创建空白辅助图。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | 如果操作成功，则返回AuxiliaryPicture实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600205](../errorcode-image.md#7600205-不支持的内存格式或像素格式) | Unsupported allocator type, e.g., use shared memory to create a gainmap as only DMA supported hdr metadata. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter, size.height or size.width is less than or equal to 0. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Alloc memory failed. |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';

function CreateAuxiliaryPictureUsingAllocator(info: image.AuxiliaryPictureInfo,  allocatorType?: image.AllocatorType, pixels?: ArrayBuffer ) {
  let res : image.AuxiliaryPicture;
  try {
    res = image.createAuxiliaryPictureUsingAllocator(info, allocatorType, pixels);
  } catch (error) {
    console.error(`Failed to create auxiliary picture using allocator=${allocatorType} and pixels=${pixels?.byteLength}.`);
  }
}

```

