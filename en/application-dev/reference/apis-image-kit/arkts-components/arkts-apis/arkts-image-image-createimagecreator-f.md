# createImageCreator

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createImageCreator

```TypeScript
function createImageCreator(width: number, height: number, format: number, capacity: number): ImageCreator
```

Creates an ImageCreator instance by specifying the image width, height, format, and capacity. Images occupy a large amount of memory. When you finish using an ImageCreator instance, call [release](arkts-image-image-imagecreator-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [createImageCreator](arkts-image-image-createimagecreator-f.md)(size: Size, format: ImageFormat, capacity: number)

**System capability:** SystemCapability.Multimedia.Image.ImageCreator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Default image width, in px. |
| height | number | Yes | Default image height, in px. |
| format | number | Yes | Image format, for example, YCBCR_422_SP or JPEG. |
| capacity | number | Yes | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageCreator](arkts-image-image-imagecreator-i.md) | ImageCreator instance. |

**Examples**

```TypeScript
let size: image.Size = {
  height: 8192,
  width: 8192
}
let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
```

```TypeScript
let creator: image.ImageCreator = image.createImageCreator(8192, 8192, image.ImageFormat.JPEG, 8);
```


## createImageCreator

```TypeScript
function createImageCreator(size: Size, format: ImageFormat, capacity: number): ImageCreator
```

Creates an ImageCreator instance by specifying the image size, format, and capacity. Images occupy a large amount of memory. When you finish using an ImageCreator instance, call [release](arkts-image-image-imagecreator-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImageCreator

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | Size | Yes | Default size of the image. |
| format | [ImageFormat](arkts-image-image-imageformat-e.md) | Yes | Image format, for example, YCBCR_422_SP or JPEG. |
| capacity | number | Yes | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageCreator](arkts-image-image-imagecreator-i.md) | ImageCreator instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; |

**Examples**

See [createImageCreator](#createimagecreator)
