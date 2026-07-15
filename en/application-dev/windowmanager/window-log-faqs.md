# Common Log Issues and Troubleshooting in Window Development

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @liangryan-->
<!--Designer: @liangryan-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=084bf627297e60b1f406ce34f5b473174466f7b3 translatedAt=2026-07-14T07:17:09.520Z pushedAt=2026-07-15T02:02:26.164Z -->

## Using the hidumper Window Command to View Window Information for Troubleshooting

**hidumper** is a diagnostic tool provided by the OpenHarmony system. It can view detailed information of all windows in the system in real time, helping you quickly locate window-related issues.

### hidumper Parameter Description

Basic command format:

```bash
hdc shell hidumper -s WindowManagerService -a '<Parameter>'
```

Parameter list:

| Parameter | Description | Command Example | Use Case |
|------|------|----------|----------|
| `-h` | Displays help information. | `hidumper -s WindowManagerService -a '-h'` | Used to view the complete parameter description when using the tool for the first time. |
| `-a` | Displays all window information. | `hidumper -s WindowManagerService -a '-a'` | Used when you need to view all windows (most common). |
| `-w {WinId}` | Displays detailed information of a specified window. | `hidumper -s WindowManagerService -a '-w 13'` | Used when the window ID is known and you need to view detailed information of a specific window. |
| `-w {WinId} {ArkUI option}` | Displays ArkUI rendering information of a specified window. | `hidumper -s WindowManagerService -a '-w 13 -arkui'` | Used when you need to view information such as the number of UI nodes and rendering status of a window. |
| `-p` | Displays the window parent-child tree structure. | `hidumper -s WindowManagerService -a '-p'` | Used to troubleshoot issues such as window parent-child relationships and hierarchy tree structures. |
| `-c` | Displays window screenshot information. | `hidumper -s WindowManagerService -a '-c'` | Used in advanced debugging scenarios (screenshot-related information). |

### Viewing All Window Lists

```bash
hdc shell hidumper -s WindowManagerService -a '-a'
```

This command outputs the complete status information of the window management service, including detailed information of all windows, focus states, z-order, and more.

Sample:

```bash
----------------------------------WindowManagerService----------------------------------
-------------------------------------ScreenGroup 1-------------------------------------
WindowName           DisplayId Pid     WinId Type Mode Flag ZOrd Orientation [ x    y    w    h    ]
SystemUi_NavigationB 0         1572    2     2112 102  0    4    0           [ 0    1208 720  72   ]
SystemUi_PrivacyIndi 0         1572    3     2111 102  0    3    0           [ 0    0    720  32   ]
SystemUi_StatusBar   0         1572    9     2108 102  0    2    0           [ 0    0    720  72   ]
note0                0         18299   13    1    1    0    1    0           [ 0    0    720  1280 ]
EntryView            0         1584    5     2001 1    0    0    8           [ 0    0    720  1280 ]
---------------------------------------------------------------------------------------  (Separator Line Between Foreground and Background Windows)
SystemUi_VolumePanel 0         1572    1     2111 1    0    -1   0           [ 0    0    0    0    ]
ScreenLockWindow     0         1572    4     2110 1    0    -1   0           [ 0    0    720  1280 ]
RecentView           0         1584    6     2115 1    0    -1   8           [ 0    0    720  1280 ]
SystemUi_DropdownPan 0         1572    7     2109 1    0    -1   0           [ 0    0    0    0    ]
SystemUi_BannerNotic 0         1572    8     2111 1    0    -1   0           [ 0    0    0    0    ]
mms0                 0         18119   11    1    1    1    -1   0           [ 0    0    720  1208 ]
camera0              0         18234   12    1    1    0    -1   0           [ 0    0    720  1280 ]
Focus window: 13
total window num: 12
```

Foreground and background windows:

In the output, foreground windows and background windows are distinguished by a separator line: windows above the separator line are foreground windows (currently displayed or interactive), and windows below the separator line are background windows (hidden or not displayed in the foreground).

Field description:

| Field | Description | Remarks |
|-------|---------|-------------|
| WindowName | Window name. | **note0** indicates a memo app window; **SystemUi_StatusBar** indicates the system status bar window. |
| DisplayId | Display device ID. | **0** indicates the primary screen. In multi‑screen scenarios, you can use [**getAllDisplays()**](../reference/apis-arkui/js-apis-display.md#displaygetalldisplays9) to query the **DisplayId** of all screens. |
| Pid | ID of the process that creates the window. | Example: **18299** |
| WinId | Window unique ID. | Example: **13** |
| Type | Window type. | This value is an internal system identifier and does not directly correspond to the [**WindowType**](../reference/apis-arkui/arkts-apis-window-e.md#windowtype7) values.<br>App windows: **1** indicates the main window; **2** indicates a child window.<br>System windows: The value is **2000+**. |
| Mode | Window mode. | **1** indicates full‑screen mode. This value is an internal system identifier and does not fully correspond to the [**WindowMode**](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#windowmode12) values. |
| Flag | Status flag. | Reserved. |
| ZOrd | Window level (z-order). | A larger value indicates a higher level (e.g., **4** is higher than **2**). **-1** indicates a hidden level. |
| Orientation | Window orientation. | Reserved. |
| [ x y w h ] | Window rectangle area. | Window position and size, with coordinates originating from the upper‑left corner of the screen. For example, **[0 0 720 1280]** indicates position **(0,0)** and size **720x1280**. |

### Viewing the Focused Window

When using the `-a` parameter to view all window information, the output displays the window that has gained focus:

```bash
hdc shell hidumper -s WindowManagerService -a '-a' | grep "Focus window"
```

Sample:

```text
Focus window: 13
```

Locate the corresponding window in the window list based on WinId: `note0` (the Notes app's main window).

Focus description for foreground and background windows:

- Only foreground windows have the opportunity to gain focus, while background windows do not gain focus.

- **ZOrd** is **-1** for background windows generally, which do not participate in focus competition.

- When a window switches from the foreground to the background, it automatically loses focus.

- You can quickly determine this using the separator line: the focus window is always in the foreground window area, and the background window area never contains a focus window.

### Viewing Detailed Information of a Specified Window

Basic command format:

Use the `-w WinId` parameter to view detailed information of a specific window:

```bash
hdc shell hidumper -s WindowManagerService -a '-w 13'
```

Output Example:

<!--RP1-->

```bash
----------------------------------WindowManagerService----------------------------------
WindowName: note0
DisplayId: 0
WinId: 13
Pid: 18299
Type: 1
Mode: 1
Flag: 0
Orientation: 0
IsStartingWindow: false
FirstFrameCallbackCalled: 1
VisibilityState: 0
Focusable: true
DecoStatus: true
IsPrivacyMode: false
isSnapshotSkip: 0
WindowRect: [ 0, 0, 720, 1280 ]
TouchHotAreas: [ 0, 0, 720, 1280 ]
```

Field description:

| Field | Meaning | Value Description |
|-------|---------|-------------------|
| WindowName | Window name. | **note0** indicates a memo app window; **SystemUi_StatusBar** indicates the system status bar window. |
| DisplayId | Display device ID. | **0** indicates the primary screen; other values indicate other screens. In multi‑screen scenarios, you can use [**getAllDisplays()**](../reference/apis-arkui/js-apis-display.md#displaygetalldisplays9) to query all screen information. |
| WinId | Window unique ID. | Example: **13** |
| Pid | ID of the process that creates the window. | Example: **18299** |
| Type | Window type. | **1** indicates an app main window; **2** indicates an app subwindow; **2000+** indicates a system window. |
| Mode | Window mode. | **1** indicates full‑screen mode. This value is an internal system identifier and does not fully correspond to the [**WindowMode**](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#windowmode12) values. |
| Flag | Status flag. | Reserved. |
| Orientation | Window orientation. | Reserved. |
| IsStartingWindow | Whether to show the launch page. | **true** indicates that the window is displaying the [app launch page](launch-page-overview.md); **false** indicates that the window is displaying normal app content. |
| FirstFrameCallbackCalled | First-frame callback status. | **0** indicates that the first-frame callback has not returned; **1** indicates that the first-frame callback has returned. |
| VisibilityState | Visibility state. | **0** indicates that the window is visible; **1** indicates that the window is hidden; **2** indicates that the window is partially visible. |
| Focusable | Whether the window can gain focus. | **true** indicates that the window can gain focus; **false** indicates that the window cannot gain focus. |
| DecoStatus | Decoration status. | **true** indicates that window decoration is enabled (with a title bar, etc.); **false** indicates that the window has no decoration. |
| IsPrivacyMode | Whether privacy mode is enabled. | **true** indicates a privacy window; **false** indicates a normal window. Privacy windows behave differently on different devices during screen capture. For details, see [Privacy Mode](./screenshot-and-privacy-mode.md#specification-and-behavior). |
| isSnapshotSkip | Whether to show the window during screen capture. | **0** indicates that the window content is displayed during screen capture; **1** indicates that the window content is not displayed during screen capture. |
| WindowRect | Window rectangle area. | Window position and size, in the format [x, y, width, height], with coordinates originating from the upper‑left corner of the screen. For example, **[0, 0, 720, 1280]** indicates position **(0,0)** and size **720x1280**. |
| TouchHotAreas | Touch hot area. | The value is in the format [x, y, width, height], with coordinates originating from the upper‑left corner of the window. |

<!--RP1End-->

Common issues:

Failed to receive keyboard inputs

- Check whether `Focusable` of the window is **false**. If so, call [setWindowFocusable()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9) and pass in **true** to enable focus.

- Check whether the window is in the foreground (above the separator line).

<!--Del-->

Window content not hidden during screenshot

- Check whether the window is a non-privacy window with the setting to display window content during screenshot, that is, **IsPrivacyMode** is **false** and **isSnapshotSkip** is **0**. In this case, the content is not hidden during screenshot.

- If you need to hide window content during screenshot, call [setWindowPrivacyMode()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowprivacymode9) and pass in **true** to enable privacy mode.

<!--DelEnd-->

Slow window startup performance

- Check whether the first frame of the window has not been displayed. If **FirstFrameCallbackCalled** is **0**, the first frame is not complete, and the page loading may be slow. You need to analyze the startup time cause in combination with logs.

<!--Del-->

Window touch area anomaly

- `TouchHotAreas` size anomaly: The touch hot area is incorrectly set.

- Compare with `WindowRect` to verify whether it is correctly set.

<!--DelEnd-->

### Locating Approach

1. Problem locating process:

   1. Identify the problem.

   2. Use hidumper to check the window state.

   3. Analyze abnormal attributes.

4. Locate the code position.

5. Fix the issue and verify the result.

2. Use with logs:

- hidumper provides real-time window status.

- System logs (**WINDOW_FROZEN_DETECTION**) provide anomaly warnings.

   - Combining both can help locate issues more quickly.

3. Comparison and verification:

   - Compare window states before and after performing an operation.

   - Confirm whether the operation takes effect.

4. Focus on key attributes:

   <!--Del-->

   - **VisibilityState**: Check whether the window is displayed.

   <!--DelEnd-->

   - **ZOrder**: Check the hierarchical relationship.

   - **WindowRect**: Check the window size and position.

> **NOTE**
>
> The **hidumper** command must be executed on a device or emulator. You can connect to the device through hdc shell and then execute the command. The hidumper output reflects the real-time window state, which may change with window operations. It is recommended to execute the query immediately when an issue occurs to obtain accurate information.

## WINDOW_FROZEN_DETECTION for Anomaly Detection

**Possible Causes**

**WINDOW_FROZEN_DETECTION** is a window pseudo freeze detection event. Devices running OpenHarmony 7.0.0 or later support this detection event.

This event is triggered when **UIContent** is not successfully set, layout anomalies occur, or similar situations arise. It provides clues for troubleshooting pseudo freeze issues, but the event being triggered does not necessarily mean that a pseudo freeze has actually occurred. Common anomaly types include: SetUIContent timeout, RectCheck err, and so on.

### Locating Window Content Loading Timeout Issues

After a window is created, the page content is not loaded within the specified time (5 seconds), causing the window to appear transparent or frozen.

**Typical logs**

Fault log format:

```text
MSG = SetUIContent timeout uid: [uid], windowName: [windowName], bundleName: [bundleName], abilityName: [abilityName]
```

Key information:

- `uid`: User ID.

- `windowName`: Window name.

- `bundleName`: Bundle name.

- `abilityName`: Instance name.

**Detection Logic**

The system starts a timer to monitor the page loading process upon window creation. If [loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) or [setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9) is not called within 5 seconds after the window is created to load page content, the system determines this as an anomaly and generates a fault log.

> **NOTE**
>
> The system's timeout detection mechanism is designed to ensure user experience and prevent users from seeing a blank window for an extended period. You should take this warning seriously and fix the issue promptly.

**Analysis, Location, and Resolution**

Troubleshooting steps:

1. Whether [loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) or [setUIContent()](../reference/apis-arkui/arkts-apis-window-Window.md#setuicontent9) is called immediately after window creation.

2. Whether there are time-consuming operations between page loading and window display.

3. Determine whether [showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9) is called before [loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9).

4. Determine whether the page path is correct.

**Positive and Negative Examples**

Negative example:

```ts
// Incorrect: Window created without loading content.
windowStage.createSubWindow('subWindow', (err, windowClass) => {
    if (err.code) {
        console.error('Failed to create sub window.');
        return;
    }
    // loadContent is not called to load the page.
    windowClass.showWindow(); // The window is shown directly, resulting in a transparent window.
});
```

Positive example:

```ts
// Positive example: Content is loaded immediately after window creation.
windowStage.createSubWindow('subWindow', (err, windowClass) => {
    if (err.code) {
        console.error('Failed to create sub window.');
        return;
    }
    // Load the page content immediately.
    windowClass.loadContent('pages/SubWindowPage', (err) => {
        if (err.code) {
            console.error('Failed to load content.');
            return;
        }
        // Show the window after the content is loaded successfully.
        windowClass.showWindow();
    });
});
```

### Locating Window Size Anomalies

Window size anomaly detection is used to identify issues where the window size exceeds a reasonable range. When the configured window size exceeds the maximum size limit, or is smaller than the minimum size limit and smaller than the screen size, the system generates a fault log.

**Typical logs**

Fault log format:

```text
RectCheck err size cur persistentId: [persistentId], windowType: [windowType], windowName: [windowName], windowState: [windowState], curWidth: [curWidth], curHeight: [curHeight], minWidth: [minWidth], minHeight: [minHeight], screenWidth: [screenWidth], screenHeight: [screenHeight], maxFloatingWindowSize: [maxFloatingWindowSize], sessionRect: [sessionRect];
```

Field description:

| Field | Description | Remarks |
|-------|---------|-------------|
| persistentId | Persistent ID. | Unique identifier of the window, used to locate a specific window. |
| windowName | Window name. | Window name set by the app. |
| windowType | Window type. | Window type value (such as app main window, subwindow, etc.). |
| windowState | Window state. | Current window state (shown, hidden, etc.). |
| curWidth | Current width (vp). | Current actual width of the window, in vp. |
| curHeight | Current height (vp). | Current actual height of the window, in vp. |
| minWidth | Minimum width limit (vp). | System-specified minimum width. This value equals the minimum width returned by [**getWindowLimitsVP()**](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) when **WindowLimits** has not been configured via [**setWindowLimits()**](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11). |
| minHeight | Minimum height limit (vp). | System-specified minimum height. This value equals the minimum height returned by [**getWindowLimitsVP()**](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) when **WindowLimits** has not been configured via [**setWindowLimits()**](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11). |
| maxFloatingWindowSize | Maximum size limit (vp). | System-specified maximum size threshold. This value equals the maximum size threshold returned by [**getWindowLimitsVP()**](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) when **WindowLimits** has not been configured via [**setWindowLimits()**](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11). |
| sessionRect | Window rectangle area (px). | Position and size of the window, in px, with coordinates originating from the upper‑left corner of the screen. |

**Detection Logic**

An anomaly is triggered when the window size meets any of the following conditions:

1. The size exceeds the maximum: `curWidth > maxFloatingWindowSize` or `curHeight > maxFloatingWindowSize`.

2. The size is below the minimum limit and smaller than the screen size (non-system window types): `curWidth < minWidth` and `curWidth < screenWidthVp`, or `curHeight < minHeight` and `curHeight < screenHeightVp`.

> **NOTE**
>
> **screenWidthVp** and **screenHeightVp** specify the screen size in vp, calculated internally by the system by dividing **screenWidth** and **screenHeight** (in px) from the fault log by the screen density. These two values are not directly output in the fault log. You can calculate them using the formula **screenWidthVp = screenWidth / density**.
>
> A WINDOW_RECT_CHECK exception indicates that the window size is outside the system-specified range. You should compare the **curWidth** and **curHeight** values in the fault log against the system limits and adjust the size parameters when calling [resize()](../reference/apis-arkui/arkts-apis-window-Window.md#resize9). **maxFloatingWindowSize** is the maximum size threshold specified by the system. Both the maximum width and maximum height of the window are limited to this value, meaning the window width must be within [minWidth, maxFloatingWindowSize] and the window height must be within [minHeight, maxFloatingWindowSize].
>
> Condition 2 requires both "smaller than the minimum limit" and "smaller than the screen size" to be met simultaneously. The reason is as follows: when the window size is smaller than the minimum limit but has already reached the screen size (for example, `curWidth < minWidth` but `curWidth >= screenWidthVp`), the screen size itself is small and the window already fills the screen and cannot be enlarged further. This is a device limitation rather than a configuration issue, so the system does not report a RectCheck error. Only when the window size is both smaller than the minimum limit and smaller than the screen size does it indicate that the window size is set too small, requiring a larger size and adjustment.

**Analysis, Location, and Resolution**

1. Obtain the fault log. View the fault log through DevEco Studio's FaultLog or hdc:

   ```bash
   hdc shell hilog | grep "RectCheck err"
   ```

2. Parse the fault log fields. Extract key information from the fault log:

   - `windowName`: Confirm the name of the abnormal window.

   - `curWidth` and `curHeight`: View the current abnormal size values (vp).

   - `minWidth`, `minHeight`, and `maxFloatingWindowSize`: Compare against the limit thresholds (vp).

   - `screenWidth` and `screenHeight`: Compare against the screen size (px, which needs to be converted to vp)

3. Determine the anomaly type. Based on the comparison of **curWidth** and **curHeight** with the limit values and screen size:

   - If `curWidth > maxFloatingWindowSize` or `curHeight > maxFloatingWindowSize`: The window size exceeds the maximum limit.

   - If `curWidth < minWidth` and `curWidth < screenWidthVp`: The window width is too small and less than the screen width.

   - If `curHeight < minHeight` and `curHeight < screenHeightVp`: The window height is too small and less than the screen height.

4. Check the size parameters at the [resize()](../reference/apis-arkui/arkts-apis-window-Window.md#resize9) call location in the code.

5. Verify the size calculation logic during window mode switching.

6. Use hidumper to verify the window state after the fix.

**Positive and Negative Examples**

Negative example:

```ts
// Incorrect: Window size is too small.
let windowClass = await windowStage.createSubWindow('subWindow');
windowClass.resize(50, 50); // The size is smaller than the minimum limit, triggering a WINDOW_RECT_CHECK exception.
windowClass.showWindow();
```

Positive example:

```ts
// Positive example: Query the system limits first, then set the size within the specified range.
let windowClass = await windowStage.createSubWindow('subWindow');
// Query the window size limit range via getWindowLimits.
let windowLimits = windowClass.getWindowLimits();
// Ensure the set size is within [windowLimits.minWidth, windowLimits.maxWidth] and [windowLimits.minHeight, windowLimits.maxHeight].
windowClass.resize(720, 640);
windowClass.showWindow();
```

## 1300002 Error Code Location Guide

Error code 1300002 indicates an abnormal window state or an invalid window object.

### Called on Window Destruction: Crash When Calling getLastWindow

During window destruction (such as **onWindowStageDestroy**, page destruction, etc.), calling the [getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1) API causes the app to crash.

**Typical logs**

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

- Error Code: 1300002

- Stack: **getLastWindow()** call location

- File name and line number: locate the specific code location

**Analysis and Location and Resolution**

Based on the log stack, locate the call location of **getLastWindow()**, and check whether it is in the destruction process (**onWindowStageDestroy**, **aboutToDisappear**, etc.). Common scenario: [loadContent()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) is not called to load the page during window creation, and **getLastWindow** is incorrectly called during the destruction process, causing a crash.

Key points:

- The **getLastWindow()** call location is not within destruction callbacks such as **onWindowStageDestroy**, **aboutToDisappear**, or **onDestroy**.

- Asynchronous tasks do not execute **getLastWindow()** after destruction.

**Positive and Negative Examples**

Negative example:

```ts
// Incorrect: The page is not loaded during window creation, and getLastWindow is called during the destruction process.
onWindowStageCreate(windowStage: window.WindowStage) {
    // Missing: loadContent is not called to load the page.
    windowStage.getMainWindow((err, win) => {
        win.showWindow(); // Directly display an empty window.
    });
}

onWindowStageDestroy() {
    let lastWindow = window.getLastWindow(this.context); // Crash!
}
```

Positive example:

```ts
// Correct: Load the page immediately upon window creation, and only perform resource cleanup during the destruction process.
onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.getMainWindow((err, win) => {
        win.loadContent('pages/MainPage'); // Load the page upon creation.
    });
}

onWindowStageDestroy() {
    this.cleanupResources(); // Only perform resource cleanup without calling getLastWindow.
}
```

### Subwindow Failed to Call setResizeByDragEnabled

When you call the [setResizeByDragEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setresizebydragenabled14) API on a subwindow to enable drag resizing, error code 1300002 is returned and the drag resize feature cannot be implemented.

**Typical logs**

View the error log through DevEco Studio or hdc:

```bash
hdc shell hilog | grep -i -E "1300002|setResizeByDragEnabled"
```

Typical log example:

``` text
SetResizeByDragEnabled: This is not main window or decor enabled sub window
```

Key information:

- Error code: 1300002 (abnormal window state)

- Error message: This is not main window or decor enabled sub window

- Cause: The subwindow does not have the title bar enabled, so drag resize is not supported.

**Analysis and Location and Resolution**

Check whether <code>decorEnabled</code> is set to <code>true</code> in <b>SubwindowOptions</b> when creating the subwindow.

For the subwindow that calls this API, ensure that the window title bar is enabled.

**Positive and Negative Examples**

Negative example:

```ts
windowStage.createSubWindowWithOptions('mySubWindow', {
  title: "",
  decorEnabled: false,    // Incorrect: Title bar not enabled
  isModal: false,
  maximizeSupported: true
});
```

Positive example:

```ts
let options: window.SubWindowOptions = {
  title: "",
  decorEnabled: true,   // Enable the window title bar.
  isModal: false,
  maximizeSupported: true
};
windowStage.createSubWindowWithOptions('mySubWindow', options).then((windowClass) => {
  // The call can be made normally when decorEnabled is true.
  windowClass.setResizeByDragEnabled(true, (err: BusinessError) => {
    console.error("setResizeByDragEnabled failed.", ` code: ${err.code}, message: ${err.message}`)
  })
})
```

### App Crashes When findWindow Is Called with a Non-existent Window Name

When you call [findWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowfindwindow9) to search for a non-existent window, the app crashes.

**Typical logs**

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

- Stack: **findWindow()** call location

- File name and line number: Locate the position of specific code.

**Analysis, Location, and Resolution**

1. Based on the log stack, locate the **findWindow()** call location and check whether the window name is correct. Use the following command to find the **findWindow** parameter:

   ```bash
   grep -n "findWindow" src/**/*.ts
   ```

2. Use hidumper to verify the window status:

   ```bash
   hdc shell hidumper -s WindowManagerService -a '-a'
   ```

**Positive and Negative Examples**

Negative example:

```ts
// Error: An incorrect window name is passed when searching for the window.
const currWindow = window.findWindow("test_Window");
// Error: A function is called on a null object.
currWindow.showWindow();
```

Positive example:

```ts
// Correct: Perform a null check on the object obtained after findWindow.
const currWindow = window.findWindow("test_Window");
if (currWindow) {
    currWindow.showWindow();
} else {
    console.error('Window not found');
}
```

### Subwindow Creation with Same Name Fails Due to Incomplete Destruction

After creating a window object using [createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9), [destroyWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#destroywindow9) is called. Before the window is fully destroyed, [createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9) is called again with the same name, causing window creation to fail with error code 1300002.

**Typical logs**

Fault log format:

```text
WindowSessionCreateCheck: WindowName(TestSubWindow) already exists.
Error code: 1300002
```

Key information:

- Duplicate window name: TestSubWindow

- Error code: 1300002

**Analysis and Location and Resolution**

The **destroyWindow()** API is used to destroy the corresponding window instance. This API is asynchronous. If the window instance to be destroyed has not been fully destroyed when **createSubWindow** is called, a window with the same name may be created, triggering error 1300002.

1. Locate the call location of **createSubWindow()** based on the log stack, find all **createSubWindow** call locations, and check whether the same window name is used:

   ```bash
   grep -n "createSubWindow" src/**/*.ts
   ```

2. After the window creation fails, use hidumper to check the current window status.

   ```bash
   hdc shell hidumper -s WindowManagerService -a '-a'
   ```

Key points:

- Ensure that the asynchronous callback is awaited after **destroyWindow()** is called. Use **await** to wait for the destruction to complete.

- Alternatively, use a different window name to avoid duplication.

**Positive and Negative Examples**

Negative example:

```ts
let windowClass: window.Window | undefined = undefined;

let windowClass = await windowStage.createSubWindow('mySubWindow');

// Incorrect: destroyWindow is an asynchronous API, but it is used as a synchronous API.
windowClass.destroyWindow();
let newWindow = await windowStage.createSubWindow('mySubWindow'); // Error code 1300002 may be returned here.
```

Positive example:

```ts
// Correct: Wait for the destruction to complete before creating.
let windowClass = await windowStage.createSubWindow('mySubWindow');

// Call destroy and wait for completion.
await windowClass.destroyWindow();
// After ensuring the destruction is complete, create a window with the same name.
let newWindow = await windowStage.createSubWindow('mySubWindow');
```

Use a different window name to avoid duplication.

```ts
// Use a timestamp as part of the window name to avoid duplication.
let windowName = 'mySubWindow_' + Date.now();
let windowClass = await windowStage.createSubWindow(windowName);
```

### Crash When Calling off('avoidAreaChange') on Window Destruction

During window destruction (such as [onWindowStageDestroy](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onwindowstagedestroy), [onDestroy](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#ondestroy), or page destruction), calling the [off('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offavoidareachange9) API causes an app crash.

**Typical logs**

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

- Stack: **off('avoidAreaChange')** call location

- File name and line number: Locate the specific code location (for example, line 50 in **MyAbility.ts**).

**Analysis, Location, and Resolution**

- Based on the log stack, locate that the **off('avoidAreaChange')** call is not in destruction callbacks such as **onWindowStageDestroy** or **onDestroy**.

- Asynchronous tasks will not execute **off('avoidAreaChange')** after destruction.

**Positive and Negative Examples**

Negative example:

```ts
// Incorrect: Call off in onWindowStageDestroy.
onWindowStageDestroy() {
    this.windowClass.off('avoidAreaChange'); // The window may have been destroyed, reporting causing the 1300002 crash error.
}
```

Positive example:

```ts
// Cancel listening when the page is hidden or before it is unloaded (non-destruction process).
onPageHide() {
  try {
    this.windowClass?.off('avoidAreaChange');
  } catch (exception) {
    console.error(`Failed to disable the listener. Cause code: ${exception.code}, message: ${exception.message}`);
  }
}
```

## 1300004 Error Code Location Guide

Error code 1300004 indicates no permission to perform the operation, commonly seen in scenarios where the window type does not match the API.

### Subwindow restore Call Failure

Calling the [restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14) API on a subwindow causes the operation to fail with error code 1300004.

**Typical logs**

Fault log:

```text
BusinessError 1300004: Unauthorized operation. Possible cause: Invalid window Type. Only main windows are supported.
```

**Analysis, Location, and Resolution**

The **restore()** API can only be used to restore the main window; otherwise, error code 1300004 is reported.

1. Use hidumper to check the window type and confirm whether the window is the main window.

    ```bash
    hdc shell hidumper -s WindowManagerService -a '-a'
    ```

2. Locate the target window in the output and check the **Type** field:

   - If **Type** is **1**, the window is the main window (**MainWindow**), and **restore()** can be called.

   - Windows with **Type** not equal to **1** cannot call **restore()**. For example, a window created through the [createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9) API is a subwindow, and the subwindow name can be specified during creation.

### Subwindow Crashes When Calling getWindowSystemBarProperties()

Call the [getWindowSystemBarProperties()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowsystembarproperties12) API on non-main windows such as subwindows or global floating windows, and error 1300004 is reported.

**Typical logs**

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

- Stack: **getWindowSystemBarProperties()** call location

- File name and line number: Locate the specific code position (for example, line 50 of **MyAbility.ts**).

**Analysis and Location and Resolution**

The **getWindowSystemBarProperties()** API is only applicable to the main window; otherwise, error code 1300004 will be reported.

1. Use hidumper to check the window type and confirm whether the current window is the main window.

    ```bash
    hdc shell hidumper -s WindowManagerService -a '-a'
    ```

2. Locate the target window in the output and check the **Type** field. If **Type** is **1**, it is a main window and **getWindowSystemBarProperties()** can be called; otherwise, **getWindowSystemBarProperties()** cannot be called.

**Positive and Negative Examples**

Negative example:

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

Positive example:

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

## 1300012 Abnormal PiP Window State

Error code 1300012 indicates an abnormal PiP window state.

### Possible Causes

- The PiP window has been destroyed, but the code is still attempting to access it.

- The PiP window is in an invalid state (for example, not yet created, already closed, or being destroyed).

- After the PiP window is destroyed, the window object is accessed in an asynchronous task or callback.

- The PiP window has already been started or is being started, but the code is still attempting to start the PiP window again.

### Crash Caused by Accessing PiP Window After Destruction

Calling the PiP window [stopPiP()](../reference/apis-arkui/js-apis-pipWindow.md#stoppip) API after the PiP window is destroyed (for example, when the user exits PiP or the window lifecycle ends) triggers error code 1300012.

**Typical logs**

```text
Error Name: Error
Error Message: [PiPWindow][stopPiP]msg: The window is not created or destroyed.
Error code: 1300012
```

**Analysis and Location**

- Whether the **stopPiP()** API is called when the PiP lifecycle state is **ABOUT_TO_STOP** or **STOPPED**.

  In the above states, the PiP window is about to stop or has already stopped. The **stopPiP()** API cannot be called at this time.

- Whether **stopPiP()** is called in an asynchronous callback such as **setTimeout** or **Promise**, and the window may have been destroyed when the callback is executed.

  In an asynchronous callback, the PiP window may have already been destroyed, and the code does not validate the PiP window state. Calling the **stopPiP()** API at this time will cause an error.

**Positive and Negative Examples**

Negative example:

```ts
// Incorrect: The asynchronous task calls the stopPiP() API after the window is destroyed.
stopPiPTimer() {
    setTimeout(() => {
        this.pipController?.stopPiP();
    }, 1000);
}
```

Positive example:

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

### Repeated PiP Window Startup Causing a Crash

When the PiP window is already started or is being started, call the PiP window [startPiP()](../reference/apis-arkui/js-apis-pipWindow.md#startpip) API, triggering error code 1300012.

**Typical logs**

```text
Error Name: Error
Error Message: [PiPWindow][startPiP]msg: The window is already started or is about to start.
Error code: 1300012
```

**Analysis, Location, and Resolution**

- Whether the **startPiP()** API is called when the PiP lifecycle state is **ABOUT_TO_START** or **STARTED**.

In this state, the PiP window is about to start or has already started, and the **startPiP()** API cannot be called at this time.

- Whether **startPiP()** is called in an asynchronous callback such as **setTimeout** or **Promise**, and the window may have already started when the callback is executed.

In an asynchronous callback, the PiP window may have already started or be in the process of starting, and the code does not verify the PiP window state. Calling the **startPiP()** API at this time will cause an error.

**Positive and Negative Examples**

Negative example:

```ts
// Incorrect: The asynchronous task calls the startPiP() API after the window is already created.
startPiPTimer() {
    setTimeout(() => {
        this.pipController?.startPiP();
    }, 1000);
}
```

Positive example:

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