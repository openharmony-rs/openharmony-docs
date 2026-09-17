# hasIrEmitter

## Modules to Import

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## hasIrEmitter

```TypeScript
function hasIrEmitter(): Promise<boolean>
```

Checks whether the device has an infrared transmitter. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability:** SystemCapability.MultimodalInput.Input.InfraredEmitter

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** is returned if the device has an infrared emitter, and **false** is returned if the device does not have an infrared emitter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
            // Query Whether There Is an Infrared Emitter
            infraredEmitter.hasIrEmitter().then((result: boolean) => {
              console.info(`Succeeded in querying infrared emitter: ${JSON.stringify(result)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to query infrared emitter, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`)})
        })
    }
  }
}
```
