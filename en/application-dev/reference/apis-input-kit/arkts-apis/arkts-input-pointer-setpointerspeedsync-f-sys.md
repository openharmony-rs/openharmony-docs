# setPointerSpeedSync (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerSpeedSync

```TypeScript
function setPointerSpeedSync(speed: number): void
```

Sets the mouse pointer speed. This API returns the result synchronously.

**Since:** 10

<!--Device-pointer-function setPointerSpeedSync(speed: int): void--><!--Device-pointer-function setPointerSpeedSync(speed: int): void-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | number | Yes | Mouse pointer speed. The value range is [1, 20], and the default value is 10. |

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
            let speed = pointer.setPointerSpeedSync(5);
            console.info(`Succeeded in setting pointer speed.`);
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

<!--DelEnd-->
