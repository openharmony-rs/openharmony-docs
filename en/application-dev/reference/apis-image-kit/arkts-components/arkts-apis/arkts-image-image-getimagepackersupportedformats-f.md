# getImagePackerSupportedFormats

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## getImagePackerSupportedFormats

```TypeScript
function getImagePackerSupportedFormats(): string[]
```

Obtains the supported encoding formats, represented by MIME types.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Return value:**

| Type | Description |
| --- | --- |
| string[] | List of supported encoding formats (MIME types). |

**Examples**

```TypeScript
async function GetImagePackerSupportedFormats() {
    let formats = image.getImagePackerSupportedFormats();
    console.info('formats:', formats);
}
```
