# getPointerSizeSync (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getPointerSizeSync

```TypeScript
function getPointerSizeSync(): number
```

Obtains the pointer size. This API returns the result synchronously.

**Since:** 10

<!--Device-pointer-function getPointerSizeSync(): int--><!--Device-pointer-function getPointerSizeSync(): int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Mouse pointer size. The value range is [1, 7]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

<!--Del-->
**Examples**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerSize = pointer.getPointerSizeSync();
            console.info(`Succeeded in getting pointer size sync, pointerSize: ${JSON.stringify(pointerSize)}.`);
          } catch (error) {
            console.error(`Failed to get pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

<!--DelEnd-->
