# Window Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 1300001 Repeated Operation
**Error Message**<br>
Repeated operation.

**Description**<br>
This error code is reported when a repeated operation is performed.

**Possible Causes**<br>
1. The window has been created.<br>
2. The window is in the current state.

**Solution**<br>
Before creating a window, check whether the window has been created or is in the current state.

## 1300002 Abnormal Window State
**Error Message**<br>
This window state is abnormal.

**Description**<br>
This error code is reported when you operate a window in an abnormal state, for example, a window that is not created yet or has been destroyed.

**Possible Causes**<br>
The window to operate is not created or has been destroyed.

**Solution**<br>
Operate the window that exists.

### Application Crashes When getLastWindow() Is Called During Window Destruction
**Possible Causes**<br>
The application crashes when the [getLastWindow()](arkts-apis-window-f.md#windowgetlastwindow9-1) API is called during window destruction (such as using **onWindowStageDestroy** or performing page destruction).

**Typical log information**<br>
Fault log format:

```text
Error Name: Error
Error Message: [window][getLastWindow]msg: xxx
Error code: 1300002
Stack trace:
  at window.getLastWindow (WindowManagerService)
  at MyComponent.onWindowStageDestroy (MyAbility.ts:50)
```

Key information:
- Error code: 1300002
- Stack: location where **getLastWindow()** is called
- File name and line number: locate the code

**Solution**<br>
Locate the position where **getLastWindow()** is called based on the log stack and check whether the window is being destroyed (for example, in the **onWindowStageDestroy** or **aboutToDisappear** callback). Common scenario: [loadContent()](arkts-apis-window-WindowStage.md#loadcontent9) is not called to load the page when the window is created. As a result, the application crashes when **getLastWindow()** is incorrectly called during the destruction process.

Key points for resolution:
- The position where **getLastWindow()** is called is not in the destruction callbacks such as **onWindowStageDestroy**, **aboutToDisappear**, or **onDestroy**.
- The asynchronous task does not call **getLastWindow()** after destruction.

**Positive and negative cases**<br>
Negative case

```ts
// Incorrect: The page is not loaded when the window is created, and **getLastWindow()** is called in the destruction process.
onWindowStageCreate(windowStage: window.WindowStage) {
    // Missing: **loadContent** is not called to load the page.
    windowStage.getMainWindow((err, win) => {
        win.showWindow(); // The empty window is displayed directly.
    });
}

onWindowStageDestroy() {
    let lastWindow = window.getLastWindow(this.context); // The application crashes.
}
```

Positive case

```ts
// Correct: The page is loaded immediately when the window is created. The destruction process only clears resources.
onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.getMainWindow((err, win) => {
        win.loadContent('pages/MainPage'); // Load the page during window creation.
    });
}

onWindowStageDestroy() {
    this.cleanupResources(); // Only clear resources. Do not call getLastWindow.
}
```

### Failed to Call setResizeByDragEnabled in a Subwindow
**Possible Causes**<br>
When you call the [setResizeByDragEnabled()](arkts-apis-window-Window.md#setresizebydragenabled14) API in a subwindow to enable window resizing by dragging, error code 1300002 is returned, and the resizing cannot be implemented.

**Typical log information**<br>
View the error log in DevEco Studio or using the hdc tool:

```bash
hdc shell hilog | grep -i -E "1300002|setResizeByDragEnabled"
```

Typical log example:

``` text
SetResizeByDragEnabled: This is not main window or decor enabled sub window
```

Key information:
- Error code: 1300002 (Abnormal Window State)
- Error message: This is not main window or decor enabled sub window
- Cause: The title bar is not enabled for the subwindow, and the subwindow does not support resizing by dragging.

**Solution**<br>
Check whether `decorEnabled` is set to `true` in **SubWindowOptions** when creating a subwindow.

For the subwindow that calls this API, ensure that the title bar has been enabled for the subwindow.

**Positive and negative cases**<br>
Negative case

```ts
windowStage.createSubWindowWithOptions('mySubWindow', {
  title: "",
  decorEnabled: false, // Incorrect: The title bar is not enabled.
  isModal: false,
  maximizeSupported: true
});
```

Positive case

```ts
let options: window.SubWindowOptions = {
  title: "",
  decorEnabled: true,   // The title bar is enabled.
  isModal: false,
  maximizeSupported: true
};
windowStage.createSubWindowWithOptions('mySubWindow', options).then((windowClass) => {
  // The API can be called properly when decorEnabled is set to true.
  windowClass.setResizeByDragEnabled(true, (err: BusinessError) => {
    console.error("setResizeByDragEnabled failed.", ` code: ${err.code}, message: ${err.message}`)
  })
})
```

### Application Crashes When findWindow() Is Called Because the Window Name Does Not Exist
**Possible Causes**<br>
When you call [findWindow()](arkts-apis-window-f.md#windowfindwindow9) to search for a window that does not exist, the application crashes.

**Typical log information**<br>
Fault log format:

```text
Error Name: Error
Error Message: [window][findWindow]msg: The window is not created or destroyed
Error code: 1300002
Stack trace:
  at window.findWindow (WindowManagerService)
  at MyComponent.onCreate (MyAbility.ts:50)
```

Key information:
- Error code: 1300002
- Stack: location where findWindow() is called
- File name and line number: locate the code

**Solution**<br>
1. Locate the position where **findWindow()** is called based on the log stack and check whether the window name is correct. Run the following command to query the **findWindow** parameter information:

   ```bash
   grep -n "findWindow" src/**/*.ts
   ```

2. Use the HiDumper to verify the window status:

   ```bash
   hdc shell hidumper -s WindowManagerService -a '-a'
   ```

**Positive and negative cases**<br>
Negative case

```ts
// Incorrect: Pass an incorrect window name when searching for a window.
const currWindow = window.findWindow("test_Window");
// Incorrect: Call a function on an empty object.
currWindow.showWindow();
```

Positive case

```ts
// Correct: Perform an empty check on the obtained object after calling findWindow.
const currWindow = window.findWindow("test_Window");
if (currWindow) {
    currWindow.showWindow();
} else {
    console.error('Window not found');
}
```

### Failed to Create a Subwindow with the Same Name Using createSubWindow Because the Destruction Is Not Complete
**Possible Causes**<br>
After creating a window object using [createSubWindow()](arkts-apis-window-WindowStage.md#createsubwindow9), you call [destroyWindow()](arkts-apis-window-Window.md#destroywindow9). Before the window is destroyed, you call [createSubWindow()](arkts-apis-window-WindowStage.md#createsubwindow9) again with the same name. As a result, the window fails to be created, and error code 1300002 is reported.

**Typical log information**<br>
Fault log format:

```text
WindowSessionCreateCheck: WindowName(TestSubWindow) already exists.
Error code: 1300002
```

Key information:
- Duplicate window name: TestSubWindow
- Error code: 1300002

**Solution**<br>
The **destroyWindow()** API is used to destroy a window instance. This API is an asynchronous API. If the window instance to be destroyed has not been destroyed when the **createSubWindow** API is called, a window with the same name may be created, triggering error code 1300002.

1. Locate the position where **createSubWindow()** is called based on the log stack, search for all positions where **createSubWindow()** is called, and check whether the same window name is used.

   ```bash
   grep -n "createSubWindow" src/**/*.ts
   ```

2. After the window fails to be created, use the HiDumper to check the current window status.

   ```bash
   hdc shell hidumper -s WindowManagerService -a '-a'
   ```

Key points for resolution:
- Ensure that the asynchronous callback is complete after **destroyWindow()** is called. Use **await** to wait until the destruction is complete.
- Use different window names to avoid duplicate names.

**Positive and negative cases**<br>
Negative case

```ts
let windowClass: window.Window | undefined = undefined;

let windowClass = await windowStage.createSubWindow('mySubWindow');

// Incorrect: destroyWindow is an asynchronous API but is used as a synchronous API.
windowClass.destroyWindow();
let newWindow = await windowStage.createSubWindow('mySubWindow'); // Error code 1300002 may be returned.
```

Positive case

```ts
// Correct: Create a window after the destruction is complete.
let windowClass = await windowStage.createSubWindow('mySubWindow');

// Call the destruction API and wait until the destruction is complete.
await windowClass.destroyWindow();
// Ensure that the window with the same name is created only after the destruction is complete.
let newWindow = await windowStage.createSubWindow('mySubWindow');
```

Use different window names to avoid duplicate names.

```ts
// Use a timestamp as part of the window name to avoid duplicate names.
let windowName = 'mySubWindow_' + Date.now();
let windowClass = await windowStage.createSubWindow(windowName);
```

### Application Crashes When off('avoidAreaChange') Is Called During Window Destruction
**Possible Causes**<br>
You call the [off('avoidAreaChange')](arkts-apis-window-Window.md#offavoidareachange9) API during window destruction (such as using [onWindowStageDestroy](../apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagedestroy), [onDestroy](../apis-ability-kit/js-apis-app-ability-uiAbility.md#ondestroy), or page destruction), the application crashes.

**Typical log information**<br>
```text
Error Name: Error
Error Message: [window][off]msg: Unregister listener failed.
Error code: 1300002
Stack trace:
  at windowClass.off('avoidAreaChange') (WindowManagerService)
  at MyComponent.onWindowStageDestroy (MyAbility.ts:50)
```

Key information:
- Error code: 1300002
- Stack: location where **off('avoidAreaChange')** is called
- File name and line number: locate the code (for example, line 50 in **MyAbility.ts**).

**Solution**<br>
- According to the log stack, the location where **off('avoidAreaChange')** is called is not in the destruction callback such as **onWindowStageDestroy** or **onDestroy**.
- The asynchronous task does not execute **off('avoidAreaChange')** after destruction.

**Positive and negative cases**<br>
Negative case

```ts
// Incorrect: Call off in onWindowStageDestroy.
onWindowStageDestroy() {
    this.windowClass.off('avoidAreaChange'); // The window may have been destroyed. Error code 1300002 is returned, and the application crashes.
}
```

Positive case

```ts
// Cancel the listener before the page is hidden or the application is uninstalled (not in the destruction process).
onPageHide() {
  try {
    this.windowClass?.off('avoidAreaChange');
  } catch (exception) {
    console.error(`Failed to disable the listener. Cause code: ${exception.code}, message: ${exception.message}`);
  }
}
```

## 1300003 Abnormal Window Manager Service
**Error Message**<br>
This window manager service works abnormally.

**Description**<br>
This error code is reported when the window manager service is abnormal.

**Possible Causes**<br>
The internal services of the window are not started normally.

**Solution**<br>
System service error. Try again later or restart the device.

## 1300004 Unauthorized Operation
**Error Message**<br>
Unauthorized operation.

**Description**<br>
This error code is reported when the API does not have the required permissions to operate an object.

**Possible Causes**<br>
1. The window object of another process is operated.<br>
2. The window type is not supported.

**Solution**<br>
1. Ensure that you are interacting only with windows created within your own process. If you are referencing windows from other processes, remove those references or calls.<br>
2. Ensure that the related operations are consistent with the supported window type.

### Failed to Call restore in a Subwindow
**Possible Causes**<br>
You call the [restore()](arkts-apis-window-Window.md#restore14) API for a subwindow, resulting in an operation failure and error code 1300004.

**Typical log information**<br>
Fault log:

```text
BusinessError 1300004: Unauthorized operation. Possible cause: Invalid window Type.Only main windows are supported.
```

**Solution**<br>
The `restore()` API can be used to restore only the main window. Otherwise, error code 1300004 will be reported.

1. Use the HiDumper to check the window type and determine whether the window is the main window.

    ```bash
    hdc shell hidumper -s WindowManagerService -a '-a'
    ```

2. Search for the target window in the output and determine the window type based on the **Type** field.
   - If the value of **Type** is **1**, the window is the main window. In this case, you can call **restore()**.
   - If the value of **Type** is not **1**, the window cannot call **restore()**. For example, a window created using the [createSubWindow()](arkts-apis-window-WindowStage.md#createsubwindow9) API is a subwindow. You can specify the subwindow name when creating the window.

### Application Crashes When getWindowSystemBarProperties Is Called in a Subwindow
**Possible Causes**<br>
When you call the [getWindowSystemBarProperties()](arkts-apis-window-Window.md#getwindowsystembarproperties12) API in a non-main window of the application, such as a subwindow or a global floating window, error code 1300004 is reported.

**Typical log information**<br>
```text
Error Name: Error
Error Message: [window][getWindowSystemBarProperties]msg: Invalid window type. Only main windows are supported.
Error code: 1300004
Stack trace:
  at windowClass.getWindowSystemBarProperties() (WindowManagerService)
  at MyComponent.onWindowStageCreate (MyAbility.ts:50)
```

Key information:
- Error code: 1300004
- Stack: location where **getWindowSystemBarProperties()** is called
- File name and line number: locate the code (for example, line 50 in **MyAbility.ts**).

**Solution**<br>
The **getWindowSystemBarProperties()** API can be called only in the main window of an application. Otherwise, error code 1300004 will be reported.

1. Use the HiDumper to check the window type and determine whether the current window is the main window of the application.

    ```bash
    hdc shell hidumper -s WindowManagerService -a '-a'
    ```
2. Search for the target window in the output and determine the window type based on the **Type** field. If the value of **Type** is **1**, the window is the main window and **getWindowSystemBarProperties()** can be called. Otherwise, **getWindowSystemBarProperties()** cannot be called.

**Positive and negative cases**<br>
Negative case

```ts
windowStage.createSubWindow('mySubWindow', (err: BusinessError, data) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to create the subwindow. Cause code: ${err.code}, message: ${err.message}`);
    return;
  }
  windowClass = data;
  console.info(`Succeeded in creating the subwindow. Data: ${JSON.stringify(data)}`);
  if (!windowClass) {
    console.info('Failed to load the content. Cause: windowClass is null');
  }
  let systemBarProperty = windowClass.getWindowSystemBarProperties()
});
```

Positive case

```ts
onWindowStageCreate(windowStage: window.WindowStage) {
  let windowClass = windowStage.getMainWindowSync();
  try {
    let systemBarProperty = windowClass.getWindowSystemBarProperties();
    console.info('Success in obtaining system bar properties. Property: ' + JSON.stringify(systemBarProperty));
  } catch (err) {
    console.error(`Failed to get system bar properties. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## 1300005 Abnormal WindowStage
**Error Message**<br>
This window stage is abnormal.

**Description**<br>
This error code is reported when you operate a WindowStage in the abnormal state, for example, a WindowStage that has been destroyed.

**Possible Causes**<br>
The WindowStage is not created or has been destroyed.

**Solution**<br>
Before operating a WindowStage, check whether it exists.

## 1300006 Abnormal Window Context
**Error Message**<br>
This window context is abnormal.

**Description**<br>
This error code is reported when you operate a window context in the abnormal state, for example, a window context that has been destroyed.

**Possible Causes**<br>
The window context has been destroyed when being operated.

**Solution**<br>
Before operating the window context, check whether it exists.

<!--Del-->
## 1300007 Application Startup Failure by WindowExtensionAbility

**Error Message**<br>
Failed to start the ability.

**Description**<br>
This error code is reported when a WindowExtensionAbility fails to start an application.

**Possible Causes**<br>
Incorrect parameters are passed into the API used by the WindowExtensionAbility to start the application.

**Solution**<br>
Pass in the correct parameters.
<!--DelEnd-->

<!--Del-->
## 1300008 Display Device Exception

**Error Message**<br>
The display device is abnormal.

**Description**<br>
This error code is reported when the display device is abnormal.

**Possible Causes**<br>
1. The display device is not ready.<br>
2. The display device is removed.<br>
3. The display device is damaged.

**Solution**<br>
Ensure that the display device is normal.
<!--DelEnd-->

## 1300009 Invalid Parent Window

**Error Message**<br>The parent window is invalid.

**Description**<br>This error code is reported when the parent window is invalid.

**Possible Causes**<br>
1. No parent window is bound.<br>
2. The parent window bound is abnormal. For example, the parent window has been destroyed.

**Solution**<br>
1. Ensure that the subwindow is bound to the parent window.<br>
2. Ensure that the status of the parent window is normal.

## 1300010 Unsupported Operation in the Current Window Mode

**Error Message**<br>The operation in the current window status is invalid.

**Description**<br>This error code is reported when the operation is not supported in the current window mode.

**Possible Causes**<br>
1. Perform the move operation in the full-screen or split-screen window.<br>
2. Perform the resize operation in the full-screen or split-screen window.

**Solution**<br>
1. Do not move the full-screen or split-screen window.<br>
2. Do not resize the full-screen or split-screen window.

## 1300011 Failure in Destroying a PiP Window

**Error Message**<br>
Failed to destroy the PiP window.

**Description**<br>
This error code is reported when destroying a PiP window fails.

**Possible Causes**<br>
The pointer to the PiP window is null.<br>

**Solution**<br>
No action is required.

## 1300012 Abnormal PiP Window Status

**Error Message**<br>
The PiP window state is abnormal.

**Description**<br>
This error code is reported when the PiP window status is abnormal.

**Possible Causes**<br>
1. The PiP window has been destroyed, but the code is still trying to access the window.<br>
2. The PiP window is in an invalid state (for example, it has not been created, has been closed, or is being destroyed).<br>
3. After the PiP window is destroyed, the window object is accessed in an asynchronous task or callback.<br>
4. The PiP window has been started or is being started, but the code is still trying to start the PiP window again.

**Solution**<br>
1. Do not call **stopPiP()** when the PiP window lifecycle state is **ABOUT_TO_STOP** or **STOPPED**.<br>
2. Do not call **startPiP()** when the PiP window lifecycle state is **ABOUT_TO_START** or **STARTED**.<br>
3. In asynchronous callbacks such as **setTimeout** and **Promise**, call **stopPiP()** or **startPiP()** only after verifying the PiP window status.

### Application Crash Caused by Accessing the PiP Window After It Is Destroyed
**Possible Causes**<br>
After the PiP window is destroyed (for example, the user exits the PiP window or the window lifecycle ends), you call the [stopPiP()](js-apis-pipWindow.md#stoppip) API of the PiP window, triggering error code 1300012.

**Typical log information**<br>
```text
Error Name: Error
Error Message: [PiPWindow][stopPiP]msg: The window is not created or destroyed.
Error code: 1300012
```

**Solution**<br>
- Check whether the **stopPiP()** API is called when the PiP window is in `ABOUT_TO_STOP` or `STOPPED` state.

  In the preceding state, the PiP window is about to stop or has stopped. In this case, the **stopPiP()** API cannot be called.

- Check whether the **stopPiP()** API is called in asynchronous callbacks such as `setTimeout` and `Promise`, and whether the window may have been destroyed when the callback is executed.

  In asynchronous callbacks, the PiP window may have been destroyed, and the code does not verify the PiP window status. In this case, calling the **stopPiP()** API will cause an error.

**Positive and negative cases**<br>
Negative case

```ts
// Incorrect: The asynchronous task calls the **stopPiP()** API after the window is destroyed.
stopPiPTimer() {
    setTimeout(() => {
        this.pipController?.stopPiP();
    }, 1000);
}
```

Positive case
```ts
async stopPiPSafely(pipController: PiPController) {
  let state: string = 'undefined';
  
  pipController.on('stateChange', (newState: string, reason: string) => {
    state = newState;
    if (state === 'STARTED') {
      pipController?.stopPiP();
    }
  });
}
```

### Application Crash Caused by Repeatedly Starting the PiP Window
**Possible Causes**<br>
When the PiP window has been started or is being started, you call the [startPiP()](js-apis-pipWindow.md#startpip) API of the PiP window, triggering error code 1300012.

**Typical log information**<br>
```text
Error Name: Error
Error Message: [PiPWindow][startPiP]msg: The window is already started or is about to start.
Error code: 1300012
```

**Solution**<br>
- Check whether the **startPiP()** API is called when the PiP window lifecycle state is `ABOUT_TO_START` or `STARTED`.

  In this state, the PiP window is about to start or has started. In this case, the **startPiP()** API cannot be called.

- Check whether the **startPiP()** API is called in asynchronous callbacks such as `setTimeout` and `Promise`, and whether the window may have been started when the callback is executed.

  In asynchronous callbacks, the PiP window may have been started or is being started, and the code does not verify the PiP window status. In this case, calling the **startPiP()** API will cause an error.

**Positive and negative cases**<br>
Negative case

```ts
// Incorrect: The asynchronous task calls the **startPiP()** API after the window is created.
startPiPTimer() {
    setTimeout(() => {
        this.pipController?.startPiP();
    }, 1000);
}
```

Positive case
```ts
async startPiPSafely(pipController: PiPController) {
  let state: string = 'undefined';
  
  pipController.on('stateChange', (newState: string, reason: string) => {
    state = newState;
    if (state === 'STOPPED') {
      pipController?.startPiP();
    }
  });
}
```

## 1300013 Failure in Creating a PiP Window

**Error Message**<br>
Failed to create the PiP window.

**Description**<br>
This error code is reported when creating a PiP window fails.

**Possible Causes**<br>
1. Incorrect parameters are passed in to create the PiP window.<br>
2. Attempt to start PiP in a non-full-screen window.

**Solution**<br>
1. Correct the input parameters.<br>
2. Do not start PiP in a non-full-screen window.

## 1300014 PiP Internal Error

**Error Message**<br>
PiP internal error.

**Description**<br>
This error code is reported when an internal error occurs in PiP.

**Possible Causes**<br>
1. The window on which the PiP feature depends is abnormal or empty.<br>
2. The PiP controller is abnormal.

**Solution**<br>
No action is required.

## 1300015 Repeated PiP Operations

**Error Message**<br>
Repeated PiP operation.

**Description**<br>
This error code is reported when a repeated PiP operation is performed.

**Possible Causes**<br>
The PiP window has been started or closed.

**Solution**<br>
Do not start or stop PiP repeatedly.<br>

## 1300016 Parameter Verification Error

**Error Message**

Parameter validation error.

**Description**

This error code is reported when parameters are incorrect. For example, the parameter value exceeds the allowed range, the length of the string or array does not meet the requirements, or the parameter format is incorrect.

**Possible Causes**

1. The parameter value is out of range.

2. The parameter length exceeds the allowed limits.

3. The parameter format is incorrect.

**Solution**

Verify that the parameters adhere to the required standards.

## 1300018 API Call Timeout

**Error Message**

API call timed out.

**Description**

This error code is reported when the API call times out.

**Possible Causes**

The wait time for a synchronous API call exceeds the upper limit.

**Solution**

The solution will vary based on the specific context. Typical approaches are:

1. Retry the API call a limited number of times.

2. Implement fallback measures, such as using cached data or alternative logic.

3. Abort the current processing logic.

## 1300019 Floating Ball Parameter Verification Error

**Error Message**

Wrong parameters for operating the floating ball.

**Description**

This error code is reported when parameters are incorrect. For example, the parameter value exceeds the allowed range, the length of the string or array does not meet the requirements, or the parameter format is incorrect.

**Possible Causes**

1. The parameter value is out of range.

2. The parameter length exceeds the allowed limits.

3. The parameter format is incorrect.

4. A mandatory parameter is not passed.

**Solution**

1. Ensure that the parameter value is within the allowed range.

2. Ensure that the parameter length is within the allowed limits.

3. Use the correct format for parameters.

4. Check whether any mandatory parameter is not passed.

For details about the floating ball parameters, see [FloatingBallParams](js-apis-floatingBall.md#floatingballparams).

## 1300020 Failure in Creating a Floating Ball Window

**Error Message**

Failed to create the floating ball window.

**Description**

This error code is reported when creating a floating ball window fails.

**Possible Causes**

1. Incorrect parameters are passed in to start the floating ball.

2. Attempt to start the floating ball on an unsupported device.

3. Attempt to start the floating ball when the application is in the background.

**Solution**

1. Check the parameters before starting the floating ball.

2. Verify that the device supports the floating ball before starting it.

3. Ensure that the application is in the foreground before starting the floating ball.

## 1300021 Failure in Starting Multiple Floating Balls

**Error Message**

Failed to start multiple floating ball windows.

**Description**

This error code is reported when starting multiple floating balls fails.

**Possible Causes**

Multiple floating ball controllers are created for the same application.

**Solution**

An application should create only one floating ball controller to start the floating ball. You are advised to use a singleton pattern to hold the floating ball controller.

## 1300022 Repeated Floating Ball Operation

**Error Message**

Repeated floating ball operation.

**Description**

This error code is reported when a repeated operation is performed on the floating ball.

**Possible Causes**

1. Attempt to start the floating ball while it is already running.

2. Attempt to stop the floating ball after it has already stopped.

3. Attempt to register the floating ball callback multiple times.

**Solution**

1. Check whether the floating ball is already running before starting it.

2. Check whether the floating ball has already stopped before stopping it.

3. Ensure that the callback is not already registered before registering the floating ball callback.

## 1300023 Internal Error of the Floating Ball

**Error Message**

Floating ball internal error.

**Description**

This error code is reported when an internal error occurs in the floating ball.

**Possible Causes**

1. The window on which the floating ball depends is abnormal or empty.

2. The floating ball controller is abnormal or empty.

**Solution**

1. Check the window of the floating ball to ensure it is not empty.

2. Check the status of the floating ball controller to ensure it is not empty.

## 1300024 Abnormal Floating Ball Window State

**Error Message**

The floating ball window state is abnormal.

**Description**

This error code is reported when the floating ball window state is abnormal.

**Possible Causes**

The floating ball window may not have been created or may have been destroyed.

**Solution**

Check that the floating ball window has been created and is not destroyed.

## 1300025 Unsupported Operation in the Current Floating Ball State

**Error Message**

The floating ball state does not support this operation.

**Description**

This error code is reported when the operation is not supported in the current floating ball state.

**Possible Causes**

1. Attempt to update the floating ball when it is not active.

2. Attempt to query window information when the floating ball is not active.

3. Attempt to launch an application window when the floating ball is not active.

4. Attempt to start the floating ball before the stop process is complete.

**Solution**

1. Check whether the floating ball is active before updating it.

2. Check whether the floating ball is active before querying window information.

3. Check whether the floating ball is active before launching an application window.

4. Wait for the floating ball to stop completely before restarting it.

## 1300026 Failure in Launch an Application Window via a Floating Ball

**Error Message**

Failed to restore the main window.

**Description**

This error code is reported when launching an application window via the floating ball fails.

**Possible Causes**

1. Incorrect parameters are passed.

2. The application does not have the `ohos.permission.AUTO_RESTORE_MAIN_WINDOW` permission and the floating ball is not tapped before the application window is launched.

3. Attempt to launch a window that belongs to another application.

**Solution**

1. Check the parameters used to launch the application window.

2. To launch the application window without user interaction, apply for the `ohos.permission.AUTO_RESTORE_MAIN_WINDOW` permission. Otherwise, launch the application window after the floating ball is tapped.

3. Launch the window that belongs to the current application.

## 1300027 Cannot Change Template Type When Updating the Floating Ball

**Error Message**

When updating the floating ball, the template type cannot be changed.

**Description**

This error code is reported when changing the template type fails.

**Possible Causes**

The template type used during the update is inconsistent with the one used during creation.

**Solution**

Ensure that the template type used when updating the floating ball matches the one used when it was created.

## 1300028 Floating Ball Based on a Static Template Cannot Be Updated

**Error Message**

Updating static template-based floating balls is not supported.

**Description**

This error code is reported when users attempt to update a floating ball based on a static template.

**Possible Causes**

Updating floating balls based on static templates is not supported.

**Solution**

Delete any existing floating balls based on static templates and create new ones.

## 1300030 Repeated Operations on the Float View

**Error Message**

Repeated operations on the float view.

**Description**

This error code is reported when operations are repeated on the float view.

**Possible Causes**

1. The float view is being started or has been started, and is started again.

2. The float view is being stopped or has been stopped, and is stopped again.

3. The float view callback is registered repeatedly.

**Solution**

1. You are advised to use [onStateChange](js-apis-floatView.md#onstatechange) to obtain the current status change. Before starting the float view, check whether the float view has been started.

2. You are advised to use [onStateChange](js-apis-floatView.md#onstatechange) to obtain the current status change. Before stopping the float view, check whether the float view has been stopped.

3. Before registering the float view callback, ensure that the callback has not been registered.

## 1300031 Operation Not Supported in the Current Float View State

**Error Message**

The floatView state does not support this operation.

**Description**

This error code is reported when the operation is not supported in the current float view state.

**Possible Causes**

1. The float view has been started but has not been stopped, and an operation that requires the float view be in stopped state (such as binding or unbinding) is performed.

2. The float view has not been started, and an operation that requires the float view be in started state (such as stopping, restoring the main window, or obtaining window attributes) is performed.

3. The float view is in stopping state, and a startup operation is performed.

**Solution**

1. Before performing an operation, check the current state of the float view to ensure that it meets the state requirements of the API.

2. To stop the float view, ensure that it has been started.

3. Wait until the float view stops (confirmed through the status change callback) and then perform the follow-up procedure.

## 1300032 Failed to Restore the Main Window

**Error Message**

Failed to restore the main window.

**Description**

This error code is reported when the float view fails to start the main window of the application.

**Possible Causes**

1. The user has never clicked the float view.

2. The float view is not displayed in the foreground.

3. The main window is in the **PAUSED** lifecycle state.

4. The main window is in the multitasking screen.

**Solution**

1. Instruct the user to click the float view and then try to restore the main window.

2. Check whether the float view is displayed in the foreground.

3. Check the lifecycle state of the main window to avoid calling the restoration API when the main window is in the **PAUSED** state.

4. Ensure that the main window is not in the multitasking state and try to restore it again.

## 1300033 Failed to Start the Float View

**Error Message**

Failed to start float view.

**Description**

This error code is reported when the float view fails to be started.

**Possible Causes**

1. Multiple float views are repeatedly started for the same application.

2. When the float view is started, the main window associated with the context is not in the foreground.

**Solution**

1. Only one float view can be started for the same application. Do not start multiple float views at the same time.

2. Before starting the float view, ensure that the application window to which the context is passed is displayed in the foreground.

## 1300034 Operation of the Float View Conflicts with Those of Other Floating Windows

**Error Message**

This operation conflicts with other floating windows.

**Description**

This error code is reported when this operation conflicts with other float views.

**Possible Causes**

The floating ball window or PiP window has been started in the application.

**Solution**

Before starting the float view, stop the floating ball window and PiP window.

## 1001 Window Null Pointer Exception<sup>(deprecated)</sup>
**Error Message**<br>
A window null pointer occurs.

**Description**<br>
This error code is reported when you operate a window pointed to by a null pointer.

**Possible Causes**<br>
A null pointer is used.

**Solution**<br>
Operate the window that exists.

## 1002 Invalid Window Type<sup>(deprecated)</sup>
**Error Message**<br>
This window type is invalid.

**Description**<br>
This error code is reported when the window type is invalid.

**Possible Causes**<br>
An invalid window type is used. For details about valid window types, see [WindowType](arkts-apis-window-e.md#windowtype7).

**Solution**<br>
Use a window type supported.

## 1003 Invalid Window Parameter<sup>(deprecated)</sup>
**Error Message**<br>
This window parameter is invalid.

**Description**<br>
This error code is reported when a window parameter is invalid.

**Possible Causes**<br>
Invalid parameters are passed in.

**Solution**<br>
Correct the parameters.

## 1004 Ability Service Exception<sup>(deprecated)</sup>
**Error Message**<br>
This system ability service works abnormally.

**Description**<br>
This error code is reported when the ability service is abnormal.

**Possible Causes**<br>
When the window is destroyed, the proxy fails to be initialized.

**Solution**<br>
Restart the device and try again.

## 1005 IPC Failure<sup>(deprecated)</sup>
**Error Message**<br>
This window IPC failed.

**Description**<br>
This error code is reported when IPC fails.

**Possible Causes**<br>
The window parameters fail to be transferred.

**Solution**<br>
Before operating a window, ensure that the client and server services in the window are normal.

## 1007 Application Startup Failure by WindowExtensionAbility<sup>(deprecated)</sup>
**Error Message**<br>
Failed to start the ability.

**Description**<br>
This error code is reported when a WindowExtensionAbility fails to start an application.

**Possible Causes**<br>
Incorrect parameters are passed into the API used by the WindowExtensionAbility to start the application.

**Solution**<br>
Pass in the correct parameters.
