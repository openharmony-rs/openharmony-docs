# getMouseScrollDirection (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getMouseScrollDirection

```TypeScript
function getMouseScrollDirection(): Promise<boolean>
```

Obtains the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously.

**Since:** 24

**Required permissions:** ohos.permission.INPUT_DEVICE_CONTROLLER

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the mouse wheel scroll direction is the same as the finger direction, and the value **false** indicates that the mouse wheel scroll direction is opposite to the finger direction. The default value is **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [3800001](../errorcode-infraredemitter.md#3800001-multimodal-input-service-internal-error) | Input service exception. |

**Examples**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('getMouseScrollDirection')
        .onClick(() => {
          try {
            // Obtain the mouse scroll direction.
            pointer.getMouseScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting mouse scroll direction, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
