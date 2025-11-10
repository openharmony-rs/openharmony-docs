# Mouse Pointer Development

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## When to Use

Mouse pointer management provides the functions such as displaying or hiding the mouse pointer as well as querying and setting the pointer style. For example, you can determine whether to display or hide the mouse pointer when a user watches a video in full screen, and can switch the mouse pointer to a color picker when a user attempts color pickup.

## Modules to Import

```js
import { pointer } from '@kit.InputKit';
```

## Available APIs

The following table lists the common APIs for mouse pointer management. For details about the APIs, see [ohos.multimodalInput.pointer](../../reference/apis-input-kit/js-apis-pointer.md).

| API                                                      | Description                                                        |
| ------------------------------------------ | ------------------------------------------------------- |
| isPointerVisible(callback: AsyncCallback\<boolean>): void | Obtains the visible status of the mouse pointer.                                |
| setPointerVisible(visible: boolean, callback: AsyncCallback\<void>): void | Sets the visible status of the mouse pointer. This setting takes effect for the mouse pointer globally.|
| setPointerStyle(windowId: number, pointerStyle: PointerStyle, callback: AsyncCallback\<void>): void | Sets the mouse pointer style. This setting takes effect for the mouse pointer style of a specified window.        |
| getPointerStyle(windowId: number, callback: AsyncCallback\<PointerStyle>): void | Obtains the mouse pointer style.                                          |

## Hiding the Mouse Pointer

When watching a video in full-screen mode, a user can hide the mouse pointer for an improved user experience.

### How to Develop

1. Switch to the full-screen playback mode.
2. Hide the mouse pointer.
3. Exit the full-screen playback mode.
4. Display the mouse pointer.

<!-- @[pointer_visible](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        Text("Click to hide the cursor")
          .onClick(() => {
            // 1. Switch to the full-screen playback mode.
            // 2. Hide the mouse pointer.
            try {
              pointer.setPointerVisible(false, (error: Error) => {
                if (error) {
                  hilog.error(DOMAIN, 'Pointer', `Set pointer visible failed, error: %{public}s`,
                    JSON.stringify(error, ["code", "message"]));
                  return;
                }
                hilog.info(DOMAIN, 'Pointer', 'Set pointer visible success.');
              });
            } catch (error) {
              hilog.error(DOMAIN, 'Pointer', `The mouse pointer hide attributes is failed. %{public}s`,
                JSON.stringify(error, ["code", "message"]));
            }
          })
		// ···

        // 3. Exit the full-screen playback mode.
        // 4. Display the mouse pointer.
        Text("Click to display pointer")
          .onClick(() => {
            try {
              pointer.setPointerVisible(true, (error: Error) => {
                if (error) {
                  hilog.error(DOMAIN, 'Pointer', `Set pointer visible failed, error: %{public}s`,
                    JSON.stringify(error, ["code", "message"]));
                  return;
                }
                hilog.info(DOMAIN, 'Pointer', 'Set pointer visible success.');
              });
            } catch (error) {
              hilog.error(DOMAIN, 'Pointer', `Set pointer visible failed, error: %{public}s`,
                JSON.stringify(error, ["code", "message"]));
            }
          })
		// ···
```


## Setting the Mouse Pointer Style

When designing a color picker, you can have the mouse pointer switched to the color picker style during color pickup and then switched to the default style on completion of color pickup. This setting takes effect for the pointer style of a specified window in the current application. A total of 43 pointer styles can be set. For details, see [Pointer Style](../../reference/apis-input-kit/js-apis-pointer.md#pointerstyle).

### How to Develop

1. Enable the color pickup function.
2. Obtain the window ID.
3. Set the mouse pointer to the color picker style.
4. End color pickup.
5. Set the mouse pointer to the default style.

<!-- @[pointer_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        Text("Click to set the mouse pointer style to the color picker style")
          .onClick(() => {
            // 1. Enable the color pickup function.
            // 2. Obtain the window ID.
            window.getLastWindow(this.getUIContext().getHostContext(),
              (error: BusinessError, windowClass: window.Window) => {
                if (error.code) {
                  hilog.error(DOMAIN, 'Pointer', 'Failed to obtain the top window. Cause: %{public}s',
                    JSON.stringify(error));
                  return;
                }
                let windowId = windowClass.getWindowProperties().id;
                if (windowId < 0) {
                  hilog.info(DOMAIN, 'Pointer', 'Invalid windowId');
                  return;
                }
                try {
                  // 3. Set the mouse pointer to the color picker style.
                  pointer.setPointerStyle(windowId, pointer.PointerStyle.COLOR_SUCKER).then(() => {
                    hilog.info(DOMAIN, 'Pointer', 'Successfully set mouse pointer style');
                  });
                } catch (error) {
                  hilog.error(DOMAIN, 'Pointer', `Failed to set the pointer style, error=%{public}s, msg=%{public}s`,
                    JSON.stringify(error), error.message);
                }
              });
          })
		// ···


        Text("Click to set the mouse pointer style to default style")
          .onClick(() => {
            // 4. End color pickup.
            window.getLastWindow(this.getUIContext().getHostContext(),
              (error: BusinessError, windowClass: window.Window) => {
                if (error.code) {
                  hilog.error(DOMAIN, 'Pointer', 'Failed to obtain the top window. Cause: %{public}s',
                    JSON.stringify(error));
                  return;
                }
                let windowId = windowClass.getWindowProperties().id;
                if (windowId < 0) {
                  hilog.info(DOMAIN, 'Pointer', 'Invalid windowId');
                  return;
                }
                try {
                  // 5. Set the mouse pointer to the default style.
                  pointer.setPointerStyle(windowId, pointer.PointerStyle.DEFAULT).then(() => {
                    hilog.info(DOMAIN, 'Pointer', 'Successfully set mouse pointer style');
                  });
                } catch (error) {
                  hilog.error(DOMAIN, 'Pointer', `Failed to set the pointer style, error=%{public}s, msg=%{public}s`,
                    JSON.stringify(error), error.message);
                }
              });
          })
```
