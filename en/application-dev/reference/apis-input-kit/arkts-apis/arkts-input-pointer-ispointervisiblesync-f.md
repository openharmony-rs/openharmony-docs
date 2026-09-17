# isPointerVisibleSync

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## isPointerVisibleSync

```TypeScript
function isPointerVisibleSync(): boolean
```

Checks whether the mouse pointer is visible in the current window. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Visible status of the mouse pointer. The value **true** indicates that the mouse pointer is visible, and the value **false** indicates the opposite. |

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
            let visible: boolean = pointer.isPointerVisibleSync();
            console.info(`Succeeded in getting pointer visible, visible: ${JSON.stringify(visible)}.`);
          } catch (error) {
            console.error(`Failed to get pointer visible, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
