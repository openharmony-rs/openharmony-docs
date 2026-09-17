# createAuxiliaryPicture

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createAuxiliaryPicture

```TypeScript
function createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture
```

Creates an AuxiliaryPicture instance based on the ArrayBuffer image data, auxiliary picture size, and auxiliary picture type. This API accepts only continuous pixel data in BGRA format and will create an auxiliary picture in RGBA format.

Images occupy a large amount of memory. When you finish using an AuxiliaryPicture instance, call [release](arkts-image-image-auxiliarypicture-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes | Image data stored in the buffer. |
| size | Size | Yes | Size of the auxiliary picture, in px. |
| type | [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | Yes | Type of the auxiliary picture. |

**Return value:**

| Type | Description |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | AuxiliaryPicture instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
async function CreateAuxiliaryPicture(context: Context) {
  let funcName = "CreateAuxiliaryPicture";
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // An HDR-compatible image is required.
  let auxBuffer: ArrayBuffer = rawFile.buffer as ArrayBuffer;
  let auxSize: image.Size = {
    height: 180,
    width: 240
  };
  let auxType: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
  let auxPictureObj: image.AuxiliaryPicture | null = image.createAuxiliaryPicture(auxBuffer, auxSize, auxType);
  if(auxPictureObj != null) {
    let type: image.AuxiliaryPictureType = auxPictureObj.getType();
    console.info(funcName, `CreateAuxiliaryPicture succeeded this.Aux_picture.type ${type}`);
  } else {
    console.error(funcName, 'CreateAuxiliaryPicture failed');
  }
}
```
