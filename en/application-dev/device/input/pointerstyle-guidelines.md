# Mouse Pointer Development

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=deff468b8adbfa4199da5cbe7b6cbc33f2bddb1e translatedAt=2026-06-24T07:41:07.597Z pushedAt=2026-06-25T06:58:22.916Z -->

## When to Use

Mouse pointer management provides the functions such as displaying or hiding the mouse pointer as well as querying and setting the pointer style. For example, you can determine whether to display or hide the mouse pointer when a user watches a video in full screen, and can switch the mouse pointer to a color picker when a user attempts color pickup.

## Modules to Import

```js
import { pointer } from '@kit.InputKit';
```

## Available APIs

The following table lists common APIs for mouse pointer management. For details, see [@ohos.multimodalInput.pointer (Mouse Pointer)](../../reference/apis-input-kit/js-apis-pointer.md).

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

<!-- @[pointer_visible](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Text("Click to hide pointer")
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
  // ...

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
  // ...
```


## Setting the Mouse Pointer Style

When you design the color picker feature, you can switch the mouse cursor style to the color picker style, and set the mouse cursor style back to the default after color selection is complete.This API sets and queries the cursor style of a specified window within the current application. A total of 49 cursor styles are available. For details, see [PointerStyle](../../reference/apis-input-kit/js-apis-pointer.md#pointerstyle).

### How to Develop

1. Enable the color pickup function.
2. Obtain the window ID.
3. Set the mouse pointer to the color picker style.
4. End color pickup.
5. Set the mouse pointer to the default style.

<!-- @[pointer_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/ArkTsPointer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
Text(`Click to set the mouse pointer style to the color picker style`)
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
  // ...


Text(`Click to set the mouse pointer style to default style`)
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