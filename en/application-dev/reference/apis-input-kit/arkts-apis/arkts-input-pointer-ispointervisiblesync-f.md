# isPointerVisibleSync

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## isPointerVisibleSync

```TypeScript
function isPointerVisibleSync(): boolean
```

Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API is called synchronously.

**Since:** 10

<!--Device-pointer-function isPointerVisibleSync(): boolean--><!--Device-pointer-function isPointerVisibleSync(): boolean-End-->

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
