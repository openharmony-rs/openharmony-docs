# shiftAppWindowTouchEvent

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## shiftAppWindowTouchEvent

```TypeScript
function shiftAppWindowTouchEvent(sourceWindowId: number, targetWindowId: number, fingerId: number): Promise<void>
```

Transfers a touchscreen input event from one window to another within the same application. This API takes effect only for the main window and its child windows. This API uses a promise to return the result.

To transfer touchscreen input events, the source window must call this API within the callback of the onTouch event (the event type must be **TouchType.Down**). After a successful call, the system sends a **TouchType.Up** event to the source window and a **TouchType.Down** event to the target window.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceWindowId | number | Yes | ID of the source window. You are advised to call [getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties) to obtain the window ID. The value must be an integer greater than 0. If it is less than or equal to 0, error code 1300016 is returned. |
| targetWindowId | number | Yes | ID of the target window. You are advised to call [getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties) to obtain the window ID. The value must be an integer greater than 0. If it is less than or equal to 0, error code 1300016 is returned. |
| fingerId | number | Yes | Unique ID of the finger in the touchscreen input event. You are advised to use the **touches** attribute in the TouchEvent object to obtain the ID. This parameter must be an integer greater than or equal to 0. If the value is less than 0, error code 1 300016 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function shiftAppWindowTouchEvent cannot work correctly due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. SourceWindow cannot find: not created or not belong to current process; 2. TargetWindow cannot find: not created or not belong to current process; 3. Internal task error. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: 1. Invalid window type. Only main windows and subwindows are supported; 2. The two windows are not from the same process. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
// ets/pages/Index.ets
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
struct Index {
  build() {
    Row() {
      Column() {
        Blank('160')
          .color(Color.Blue)
          .onTouch((event: TouchEvent) => {
            // The source window touch event type must be TouchType.Down.
            if (event.type === TouchType.Down) {
              try {
                let sourceWindowId = 1;
                let targetWindowId = 2;
                let promise = window.shiftAppWindowTouchEvent(sourceWindowId, targetWindowId, event.touches[0].id);
                promise.then(() => {
                  console.info(`Succeeded in shifting app window touch event`);
                }).catch((err: BusinessError) => {
                  console.error(`Failed to shift app window touch event. Cause code: ${err.code}, message: ${err.message}`);
                });
              } catch (exception) {
                console.error(`Failed to shift app touch event. Cause code: ${exception.code}, message: ${exception.message}`);
              }
            }
          })
      }.width('100%')
    }.height('100%').width('100%')
  }
}
```
