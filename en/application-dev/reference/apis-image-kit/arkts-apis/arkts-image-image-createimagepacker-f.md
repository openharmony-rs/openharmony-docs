# createImagePacker

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createImagePacker

```TypeScript
function createImagePacker(): ImagePacker
```

Creates an ImagePacker instance.

Images occupy a large amount of memory. When you finish using an ImagePacker instance, call [release](arkts-image-image-imagepacker-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Return value:**

| Type | Description |
| --- | --- |
| [ImagePacker](arkts-image-image-imagepacker-i.md) | ImagePacker instance created. |

**Examples**

```TypeScript
async function CreateImagePacker() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
}
```
