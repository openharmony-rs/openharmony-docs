# createPixelMapFromParcel

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMapFromParcel

```TypeScript
function createPixelMapFromParcel(sequence: rpc.MessageSequence): PixelMap
```

Creates a PixelMap object based on MessageSequence parameter.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | Yes | [rpc.MessageSequence parameter.](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc.md) |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | Returns the instance if the operation is successful. Otherwise, an exception will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-operation-failed) | Operation failed. |
| [62980097](../errorcode-image.md#62980097-pixelmap-serialization-failed) | IPC error. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid input parameter. |
| [62980105](../errorcode-image.md#62980105-failure-in-obtaining-image-data) | Failed to get the data. |
| [62980177](../errorcode-image.md#62980177-abnormal-api-environment) | Abnormal API environment. |
| [62980178](../errorcode-image.md#62980178-failure-in-creating-a-pixelmap) | Failed to create the PixelMap. |
| [62980179](../errorcode-image.md#62980179-abnormal-buffer-size) | Abnormal buffer size. |
| [62980180](../errorcode-image.md#62980180-failure-in-mapping-the-file-descriptor) | FD mapping failed. |
| [62980246](../errorcode-image.md#62980246-failure-in-reading-the-pixelmap) | Failed to read the PixelMap. |

**Examples**

```TypeScript
// EntryAbility.ets
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MySequence implements rpc.Parcelable {
  pixel_map: sendableImage.PixelMap;
  constructor(conPixelmap: sendableImage.PixelMap) {
    this.pixel_map = conPixelmap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixel_map.marshalling(messageSequence);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    try {
      this.pixel_map = sendableImage.createPixelMapFromParcel(messageSequence);
    } catch(e) {
      let error = e as BusinessError;
      console.error(`Failed to create a PixelMap from a parcel. Code: ${error.code}, message: ${error.message}.`);
      return false;
    }
    return true;
  }
}
async function CreatePixelMapFromParcel() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: 4,
    size: { height: 4, width: 6 },
    alphaType: 3
  }
  let pixelMap: sendableImage.PixelMap | undefined = undefined;
  await sendableImage.createPixelMap(color, opts).then((srcPixelMap: sendableImage.PixelMap) => {
    pixelMap = srcPixelMap;
  })
  if (pixelMap != undefined) {
    // Implement serialization.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Implement deserialization to obtain data through the RPC.
    let ret: MySequence = new MySequence(pixelMap);
    data.readParcelable(ret);

    // Obtain the PixelMap object.
    let newPixelMap = ret.pixel_map;
  }
}
```
