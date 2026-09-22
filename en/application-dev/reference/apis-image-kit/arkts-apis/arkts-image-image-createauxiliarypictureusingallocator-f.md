# createAuxiliaryPictureUsingAllocator

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createAuxiliaryPictureUsingAllocator

```TypeScript
function createAuxiliaryPictureUsingAllocator(auxiliaryPictureInfo: AuxiliaryPictureInfo,
    allocatorType?: AllocatorType, pixels?: ArrayBuffer): AuxiliaryPicture
```

Create an &lt;b&gt;AuxiliaryPicture&lt;/b&gt; object, the memory type used by the AuxiliaryPicture can be specified by allocatorType IMAGE_ALLOCATOR_TYPE. By default, the system selects the memory type based on the image type, image size, platform capability, etc. When processing the AuxiliaryPicture returned by this interface, please always consider the impact of stride. The created auxiliary picture is initialized with the input pixels.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| auxiliaryPictureInfo | [AuxiliaryPictureInfo](arkts-image-image-auxiliarypictureinfo-i.md) | Yes | The basic information of the auxiliary picture. |
| allocatorType | [AllocatorType](arkts-image-image-allocatortype-e.md) | No | Memory type. |
| pixels | ArrayBuffer | No | Pixel data used to initialize the auxiliary picture. |

**Return value:**

| Type | Description |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | The AuxiliaryPicture object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600205](../errorcode-image.md#7600205-unsupported-format) | Unsupported allocator type, e.g., use shared memory to create a gainmap as only DMA supported hdr metadata. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter, size.height or size.width is less than or equal to 0. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Alloc memory failed. |

**Examples**

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
