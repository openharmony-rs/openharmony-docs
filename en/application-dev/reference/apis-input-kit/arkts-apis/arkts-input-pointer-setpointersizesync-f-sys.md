# setPointerSizeSync (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerSizeSync

```TypeScript
function setPointerSizeSync(size: number): void
```

Sets the pointer size. This API returns the result synchronously.

**Since:** 10

<!--Device-pointer-function setPointerSizeSync(size: int): void--><!--Device-pointer-function setPointerSizeSync(size: int): void-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Mouse cursor size. The value ranges from 1 to 7, and the default value is **1**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

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
            // Set the mouse pointer size synchronously.
            pointer.setPointerSizeSync(5);
            console.info(`Succeeded in setting pointer size sync.`);
          } catch (error) {
            console.error(`Failed to set pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

<!--DelEnd-->
