# Window Z-Order

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=713e0950280e51b65f5485cb7ba4c41c0297cfd7 translatedAt=2026-11-13T12:17:22.136Z pushedAt=2026-11-16T02:06:53.365Z nl=1 -->

## When to Use

**Window z-order** (**ZOrder**) refers to the stacking order of multiple windows on the screen, which determines the front-to-back display relationship of windows.

The larger the z-order value, the closer the window is displayed to the front and can cover windows with smaller z-order values. Conversely, windows with smaller z-order values may be obscured by other windows.

For third-party apps, the z-order of a window cannot be directly modified, but the display z-order of subwindows can be indirectly affected by controlling the **zLevel** attribute.

The system controls the visibility and interaction priority of the user interface by managing **ZOrder** and **zLevel**.

This section systematically explains the window z-order management mechanism from five aspects: basic concepts, z-order rules, parent-child window relationships, the TopMost window mechanism, and related API examples.

## Basic Concepts and Z-Order Rules

### ZOrder and zLevel

**ZOrder** represents the window stacking order maintained internally by the system. The larger the value, the closer the window is to the front. Third-party apps cannot directly modify **ZOrder**.

**zLevel** represents the relative z-order between subwindows within an app that can be controlled by third-party apps, and is only effective for non-modal subwindows. The value range of zLevel is [-10000, 10000], and the default value is **0**. The greater the **zLevel** value, the larger the corresponding **ZOrder**, and the closer the window is to the front.

### Z-Order Rules for Window zLevel

- **Subwindows with different zLevels**

  - A window with a higher zLevel always covers a window with a lower zLevel. Even if a window with a lower zLevel is clicked, it will not be raised above the window with a higher zLevel.

- **Subwindows with the same zLevel**

  - By default, the window created later has a higher z-order.

  - When the user taps a subwindow, its z-order is raised to the highest position within the same zLevel, implementing "tap-to-top."

  - If [setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14) is called with **false**, the raise-on-tap feature is disabled, and the z-order remains unchanged when tapped.

### Z-Order Rules for Window Types

- **Z-order for all window types**

  The hierarchical relationship of all window types in the system, from top to bottom, is shown in the following table (levels from high to low):

  | Window category | Description |
  | -------- | -------- |
  | Picture-in-picture window | Created through the [PiPWindow.create()](../reference/apis-arkui/js-apis-pipWindow.md#pipwindowcreate) API. It is used to display video content in a small window. For example, during a video call or video playback, when you swipe up to exit the application, the screen continues to be displayed in a small window. |
  | Global floating window | A window of the [WindowType.TYPE_FLOAT](../reference/apis-arkui/arkts-apis-window-e.md#windowtype7) type created through [createWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowcreatewindow9-1). It requires the [ohos.permission.SYSTEM_FLOAT_WINDOW](../security/AccessToken/restricted-permissions.md#ohospermissionsystem_float_window) permission and is located above all application windows. |
  | Pinned main window | A main window pinned to the top by calling [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14). It is located above the normal main windows of other applications, but still lower than the picture-in-picture window and the global floating window above it. |
  | Main window | An application main window created by default. Multiple main windows are stacked in the order in which they are activated. |

  The specific values of each level vary across devices (such as PC/2-in-1 and Phone devices). The table above describes only the relative hierarchical relationship.

- **Z-order adjustment for windows of the same type**

  For windows of the same type (multiple main windows, multiple regular subwindows), the z-order can be adjusted by tapping or using shortcuts (such as **Alt+Tab**).

- **Default z-order of in-app subwindow types**

  The system assigns default z-orders to different types of subwindows. The priorities from high to low are as follows:

  | Window Type | Creation Method |
  | -------- | -------- |
  | App-modal subwindow | Call the [createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12) API and set **isModal** to **true** and **modalityType** to **APPLICATION_MODALITY** in the subwindow parameters [SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11). |
  | Toast subwindow | Call the [showToast()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showtoast) API and set **showMode** to **TOP_MOST**. |
  | Text menu subwindow | Call the [showActionMenu()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu) API and set **showInSubWindow** to **true**. |
  | Dialog subwindow | Call [openCustomDialog()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12) with dialogContent and options parameters, and set **showInSubWindow** to **true**.<br>Call [openCustomDialog()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12-1) with the options parameter, and set **showInSubWindow** to **true**.<br>Call [openCustomDialogWithController()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18), and set **showInSubWindow** to **true**. |
  | Modal subwindow | Call the [createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12) API and set **isModal** to **true** and **modalityType** to **WINDOW_MODALITY** in the subwindow parameters [SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11). |
  | Normal subwindow | The default subwindow created by calling the [createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12) API. |

  Windows of different types cannot cross their z-order ranges by tapping or through APIs.

### Z-Order Rules for Parent-Child Windows

- When a parent window is raised, all its child windows are raised along with it; when a child window is raised, its parent window is also raised.
- The z-order of a child window is always higher than that of its parent window.
- A window can be raised by calling the [raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14) API or by tapping the window.

### Z-Order Rules for TopMost Windows

- In the [freeform window](window-terminology.md#freeform-window) state, an application main window can call the [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) interface and pass in true to place itself above other application windows, achieving a persistent display effect of "not being obscured". This should be used reasonably to avoid affecting the user experience. Using this interface requires the permission [ohos.permission.WINDOW_TOPMOST](../security/AccessToken/permissions-for-all.md#ohospermissionwindow_topmost).

- Starting from API version 26.0.1, the topmost state of a main window can also be adjusted through the [setWindowPosition()](../reference/apis-arkui/arkts-apis-window-f.md#windowsetwindowposition) interface. When using this interface to set a main window as topmost or to cancel the topmost state of a main window that is currently topmost, the permission [ohos.permission.WINDOW_TOPMOST](../security/AccessToken/permissions-for-all.md#ohospermissionwindow_topmost) is required.

## Z-Order Control Mechanisms


| Feature/Operation | Control Method | Effective Scope | Applicable Scenario |
| -------- | -------- | -------- | -------- |
| Z-order | System-managed | Effective across apps | Internal rendering order management |
| zLevel | [setSubWindowZLevel()](../reference/apis-arkui/arkts-apis-window-Window.md#setsubwindowzlevel18)/set when creating the window | Effective only within the same application | Subwindow level management |
| Window topmost | [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) | Can take effect across applications | Persistent windows such as video and navigation |
| Raise by click | [setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14) | Between subwindows of the same type within the same application | Prevent accidental touches, fixed layout |

## Z-Order Related Development Scenarios

| Feature | Typical Scenario | Corresponding API |
| -------- | -------- | -------- |
| Set main window to topmost | Used to place a window above other app windows without being obscured, such as in video calls, navigation, and other scenarios. | [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) |
| Adjust the main window Z-order | Can be used to adjust the Z-order of multiple windows simultaneously, such as in cloud application scenarios. | [setWindowPosition()](../reference/apis-arkui/arkts-apis-window-f.md#windowsetwindowposition) |
| Raise a subwindow to the top | Used to raise a subwindow to the topmost position among subwindows of the same type within the current app. This only takes effect within the scope of subwindows that share the same parent window and the same **zLevel** value in the current app.<br>For example, in a video conference with a floating toolbar, the main window displays the video feed, while subwindows include a chat box, a sharing control bar, and so on. When the chat box is tapped, **raiseToAppTop()** can be called to bring it to the top, preventing it from being obscured by other subwindows. | [raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14) |
| Disable/enable the subwindow raise-on-tap feature | Can be used for tool panels with fixed layouts to prevent z-order confusion caused by accidental user operations. | [setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14) |
| Get the topmost window in the current app | Can determine the currently displayed topmost window (which may be the main window or a subwindow), used for scenarios such as logging or state synchronization. | [getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1) |

> **NOTE**
>
> - Set **zLevel** appropriately to avoid z-order conflicts.
>
> - Use the TopMost feature with caution to avoid disrupting the system's multi-window experience.
>
> - For critical interfaces that require high-priority display, you can use [raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14) to ensure visibility. Before using this API, ensure that the window has called a **showWindow()** type API ([showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9-1)/[showWindow(options: ShowWindowOptions)](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow20)) and that the call has completed.
>
> - [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) takes effect only in the [freeform window](window-terminology.md#freeform-window) state. You can use [isInFreeWindowMode()](../reference/apis-arkui/arkts-apis-window-Window.md#isinfreewindowmode22) to check whether the current window is in freeform window mode, and combine it with the [on('freeWindowModeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onfreewindowmodechange22) event listener to listen for window mode changes in real time, thereby accurately determining when it is safe to call [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14).

## Practice Cases

### Implementing Key Operation Confirmation with a Modal Subwindow

It is recommended to create a modal subwindow for key operations such as deletion, payment, and logout. These operations usually require a second confirmation from the user, and other operations on the page should be blocked until the confirmation is complete. The level of a modal subwindow is higher than that of its main window and normal subwindows. After it pops up, the windows within its occlusion range cannot be interacted with until the subwindow is closed.

1. The main window can create a modal subwindow by calling the [createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12) API and setting the isModal field to true. The default level of a modal subwindow is higher than that of a normal subwindow, so there is no need to additionally call [setSubWindowZLevel()](../reference/apis-arkui/arkts-apis-window-Window.md#setsubwindowzlevel18) to adjust the level.
   - When modalityType is set to WINDOW_MODALITY, only the parent window is occluded, which is suitable for operation confirmation within a single page.
   - When modalityType is set to APPLICATION_MODALITY, all windows of the current application are occluded, which is suitable for global blocking.
   - To cancel the modal state midway, call [setSubWindowModal()](../reference/apis-arkui/arkts-apis-window-Window.md#setsubwindowmodal12) and pass in false.
2. Call [loadContent()](../reference/apis-arkui/arkts-apis-window-Window.md#loadcontent9) to load the confirmation dialog page, and call [showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9-1) to display the subwindow.
3. After the user confirms or cancels, call [destroyWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#destroywindow9) to destroy the subwindow, and the occluded windows resume interaction.

<!-- @[modal_sub_window](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowZOrder/entry/src/main/ets/pages/Index.ets) -->

```ts
import { window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Pop up a modal window for confirming the delete operation.
async function showDeleteConfirm(context: common.UIAbilityContext): Promise<void> {
  let mainWindow = context.windowStage.getMainWindowSync();
  let options: window.SubWindowOptions = {
    title: 'Delete Confirmation',
    decorEnabled: false,
    isModal: true,
    modalityType: window.ModalityType.WINDOW_MODALITY
  };
  try {
    // Step 1: Create a modal window.
    let subWindow = await mainWindow.createSubWindowWithOptions('deleteConfirm', options);
    // Step 2: Load and display the confirmation dialog page.
    subWindow.loadContent('pages/DeleteConfirm', (err: BusinessError) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause code: ${err.code}, message: ${err.message}`);
        return;
      }
      subWindow.showWindow();
    });
  } catch (exception) {
    console.error(`Failed to create the subwindow. Cause code: ${exception.code}, message: ${exception.message}`);
  }
}
```

In step 3, the logic for destroying the modal window is located in the confirmation dialog page (DeleteConfirm.ets). After the user taps the **Cancel** or **Delete** button, the modal window is destroyed. The sample code is as follows:

<!-- @[modal_sub_window_close](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowZOrder/entry/src/main/ets/pages/DeleteConfirm.ets) -->

```ts
@Entry
@Component
struct DeleteConfirm {
  build() {
    Column({ space: 24 }) {
      Text('Are you sure you want to delete this item?')
        .fontSize(20)
        .fontWeight(FontWeight.Medium)

      Row({ space: 16 }) {
        Button('Cancel')
          .onClick(() => {
            this.destroySubWindow();
          })
        Button('Delete')
          .onClick(() => {
            // Execute the delete logic.
            this.destroySubWindow();
          })
      }
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }

  // Step 3: After the user confirms or cancels, destroy the modal window and restore interaction for the occluded window.
  private destroySubWindow(): void {
    let subWindow = window.findWindow('deleteConfirm');
    subWindow.destroyWindow().then(() => {
      console.info('Succeeded in destroying the subwindow.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to destroy the subwindow. Cause code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### Implementing Main Window Always-on-Top

In scenarios such as video calls and real-time navigation, the application main window needs persistent display without being occluded by other application windows. You can call [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) to pin it to top.

> **NOTE**
>
> - A pinned main window is only higher than the normal main windows of other applications, and is still lower than windows at higher levels (such as picture-in-picture windows and global floating windows).
> - It is recommended that you provide a clear pin/unpin entry on the page to avoid long-term pinning that interferes with the user's multitasking operations.

1. Declare the permission [ohos.permission.WINDOW_TOPMOST](../security/AccessToken/permissions-for-all.md#ohospermissionwindow_topmost) in [module.json5](../quick-start/module-configuration-file.md).

   ```json
   {
     "module": {
       "requestPermissions": [
         {
           "name": "ohos.permission.WINDOW_TOPMOST"
         }
       ]
     }
   }
   ```

2. Call [isInFreeWindowMode()](../reference/apis-arkui/arkts-apis-window-Window.md#isinfreewindowmode22) to check whether the window is currently in the [freeform window](window-terminology.md#freeform-window) state (pinning takes effect only in this state). If necessary, register [on('freeWindowModeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onfreewindowmodechange22) to listen for window mode changes.
3. Call [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) and pass in `true` to implement main window always-on-top. When the window no longer needs to be pinned, call `setWindowTopmost()` and pass in `false` to unpin it.

<!-- @[window_topmost](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowZOrder/entry/src/main/ets/pages/Index.ets) -->

```ts
// Index.ets
@Entry
@Component
struct Index {
  @State isTopmost: boolean = false;
  private context = (this.getUIContext()?.getHostContext() as common.UIAbilityContext);

  build() {
    Column({ space: 24 }) {
      // ...
      Button(this.isTopmost ? 'Cancel Topmost' : 'Set Topmost')
        .onClick(() => {
          let mainWindow = this.context.windowStage.getMainWindowSync();
          // Step 2: Confirm whether the current state is freeform window (pinning to top takes effect only in this state).
          if (!mainWindow.isInFreeWindowMode()) {
            console.info('The window is not in freeform window mode, topmost is not supported.');
            return;
          }
          // Step 3: Call setWindowTopmost() and pass in true to implement main window pinning; pass in false to unpin when the window is already always-on-top.
          this.isTopmost = !this.isTopmost;
          mainWindow.setWindowTopmost(this.isTopmost).then(() => {
            console.info('Succeeded in setting window topmost.');
          }).catch((err: BusinessError) => {
            console.error(`Failed to set window topmost. Cause code: ${err.code}, message: ${err.message}`);
          });
        })
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

