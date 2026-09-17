# setMouseScrollDirection (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setMouseScrollDirection

```TypeScript
function setMouseScrollDirection(inverted: boolean): Promise<void>
```

Sets the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously.

**Since:** 24

**Required permissions:** ohos.permission.INPUT_DEVICE_CONTROLLER

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inverted | boolean | Yes | Scroll direction of the mouse wheel.<br>The value **true** indicates that scroll direction matches the finger movement on the wheel, and the value **false** indicates that the scroll direction is opposite to the finger movement. <br>The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
      Button('setMouseScrollDirection')
        .onClick(() => {
          try {
            // Set the mouse scroll direction.
            pointer.setMouseScrollDirection(false).then(() => {
              console.info(`Succeeded in setting mouse scroll direction.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
