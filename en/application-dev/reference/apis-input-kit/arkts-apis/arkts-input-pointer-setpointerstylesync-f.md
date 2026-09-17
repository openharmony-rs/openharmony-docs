# setPointerStyleSync

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerStyleSync

```TypeScript
function setPointerStyleSync(windowId: number, pointerStyle: PointerStyle): void
```

Sets the mouse pointer style type for a specified window and returns the result synchronously. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor).

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | Window ID. The value is an integer greater than or equal to 0. <br>If the window ID is valid and the corresponding window exists, the mouse pointer style of the window can be set properly. <br>If the window ID is valid but the window does not exist, the mouse pointer style can also be set properly. <br>The result can be obtained through [getPointerStyleSync](arkts-input-pointer-getpointerstylesync-f.md). |
| pointerStyle | [PointerStyle](arkts-input-pointer-pointerstyle-e.md) | Yes | Pointer style. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api.<br> When the windowId value is -1, the system permission is required to set the global style.  **ArkTS mode:** This error code applies only to ArkTS-Sta. |

**Examples**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Obtains the most recent window within the application.
          window.getLastWindow(this.getUIContext().getHostContext(), (error: BusinessError, win: window.Window) => {
            if (error.code) {
              console.error(`Failed to obtain the top window, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              return;
            }
            let windowId = win.getWindowProperties().id;
            if (windowId < 0) {
              console.info(`Invalid windowId.`);
              return;
            }
            try {
              // Synchronously sets the mouse pointer style.
              pointer.setPointerStyleSync(windowId, pointer.PointerStyle.CROSS);
              console.info(`Succeeded in setting pointer style.`);
            } catch (error) {
              console.error(`Failed to set pointer style, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            }
          });
        })
    }
  }
}
```
