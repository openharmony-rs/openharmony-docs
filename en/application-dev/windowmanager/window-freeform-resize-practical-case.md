# Freeform Window Resize Development Practice (PC/2-in-1 Device)

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @wxcHello-->
<!--Designer: @ALTNAT-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=a670334a02fcf5fcae747328a9ce1002ca92cefb translatedAt=2026-11-12T04:53:27.673Z pushedAt=2026-11-12T07:50:18.600Z nl=1 -->

## When to Use

**Freeform window resize** refers to the ability of an application to continuously adjust the window size by dragging in the [freeform window](freeform-window-overview.md#freeform-window) state, so that multiple windows can be flexibly arranged on the same screen instead of switching among several fixed sizes.

Continuous window size changes impose additional requirements on applications: content must display correctly at any size, size limits must be reasonable, and the UI must follow in real time. This practice covers the following:

- While a window is being drag-resized, the application can sense window size changes in real time and refresh the width and height to the UI.
- Set a reasonable size range for window resize to avoid content truncation when the window is resized too small and wasted space when it is too large.
- Window content follows the window size continuously.

> **NOTE**
>
> The freeform window resize scenario mainly applies to PC/2in1 devices. It also applies to other devices (some Phone and Tablet devices) that support and are in the freeform window state.

## How to Develop

1. Declare support for freeform windows.

   In the [module.json5](../quick-start/module-configuration-file.md) configuration file, declare `"floating"` in the `supportWindowMode` attribute under the [abilities tag](../quick-start/module-configuration-file.md#abilities) so that the window supports continuous drag-to-resize in the freeform window state.

   ``` json5
   "supportWindowMode": [
     "fullscreen",
     "split",
     "floating"
   ]
   ```

2. Obtain the main window and complete initialization.

   Obtain the main window through [getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1) and complete the related initialization (performed by the encapsulated `setupWindow()` method in this example). The main operations are as follows:

   - Enable drag-to-resize: drag-to-resize is an inherent capability of the freeform window. Whether the user is allowed to drag is determined by the [setResizeByDragEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setresizebydragenabled14-1) switch. The default state of this switch is not guaranteed to be enabled. The example enables it explicitly to ensure that drag-to-resize is available as soon as the page is entered.
   - Set the size range: when a window is resized too small or too large, it can cause content truncation, layout corruption, or wasted space. You can set the size range through the [setWindowLimits()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11) API. This range is intersected with the system limits, and the effective value may be more conservative than the input parameters.
   - Synchronize the initial size: in this example, `applySize()` synchronizes the current window width and height to the UI.

   <!-- @[init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowFreeformResize/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Write the window width and height (px) back to the state variable to drive UI refresh.
   private applySize(widthPx: number, heightPx: number): void {
     this.winWidthPx = Math.round(widthPx);
     this.winHeightPx = Math.round(heightPx);
   }
   
   // Read the effective size range (the intersection of the input parameters and system limits) and store it in the state variable for UI display.
   private readLimits(win: window.Window): void {
     try {
       const l: window.WindowLimits = win.getWindowLimitsVP();   // The returned unit is vp.
       // Store the effective range in the state variable separately.
       this.limitsMinW = l.minWidth ?? 0;
       this.limitsMaxW = l.maxWidth ?? 0;
       this.limitsMinH = l.minHeight ?? 0;
       this.limitsMaxH = l.maxHeight ?? 0;
       console.info(`Effective range: ${l.minWidth}~${l.maxWidth} × ${l.minHeight}~${l.maxHeight}`);
     } catch (err) {
       console.error('Failed to read effective size range:', String(err));
     }
   }
   
   // Window initialization: enable drag-to-resize, set the size range, and synchronize the initial size.
   private setupWindow(win: window.Window): void {
     // Drag-to-resize is supported by default; enable it explicitly in case it is disabled.
     win.setResizeByDragEnabled(true).then(() => {
       console.info('Drag-to-resize enabled');
     }).catch((err: BusinessError) => {
       console.error(`setResizeByDragEnabled failed: ${err.code} ${err.message}`);
     });
   
     // Prevent excessive resizing from causing content truncation or layout corruption.
     const limits: window.WindowLimits = {
       minWidth: 480,
       minHeight: 360,
       maxWidth: 1600,
       maxHeight: 1000,
       pixelUnit: window.PixelUnit.VP
     };
     win.setWindowLimits(limits).then(() => {
       this.readLimits(win);   // Read the "intersection of the input parameters and system limits" and print the effective range.
     }).catch((err: BusinessError) => {
       console.error(`setWindowLimits failed: ${err.code} ${err.message}`);
     });
   
     // Read the initial window size and synchronize it to the UI.
     try {
       this.applySize(win.getWindowProperties().windowRect.width,
         win.getWindowProperties().windowRect.height);
     } catch (err) {
       console.error('Failed to get initial window size:', JSON.stringify(err));
     }
   }
   
   // Obtain the main window, complete initialization, and register the size change listener.
   aboutToAppear(): void {
     const ctx = this.getUIContext().getHostContext();   // Obtain the host context as the input parameter of getLastWindow.
     if (!ctx) {
       return;   // The host context cannot be obtained in environments such as the previewer. This example depends on a real window, so skip it directly.
     }
     window.getLastWindow(ctx).then((win: window.Window) => {
       this.mainWindow = win;   // Save the main window instance.
       this.setupWindow(win);   // Complete initialization: enable drag-to-resize, set the size range, and synchronize the initial size.
   
       // ...
     }).catch((err: BusinessError) => {
       console.error(`getLastWindow failed: ${err.code} ${err.message}`);
     });
   }
   
   // ...
   ```

3. Listen for window size changes and update the window width and height in real time.

   Listen for window size changes through [on('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowsizechange7). After the window is dragged or drag-resized, the system invokes the listener callback. In the callback, write the window width and height (px) back to the state variable through `applySize()` to refresh the window width and height in real time.

   When the page is destroyed, unregister the listener through [off('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offwindowsizechange7) in `aboutToDisappear` to avoid memory leaks.

   <!-- @[resizeChange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowFreeformResize/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Obtain the main window, complete initialization, and register the size change listener.
   aboutToAppear(): void {
     // ...
   
       // Size change callback: write the new width and height back to the state variable to drive UI refresh.
       this.sizeListener = (size: window.Size): void => {
         this.applySize(size.width, size.height);
       };
       // Register the listener; sizeListener is invoked after the window is dragged or drag-resized.
       try {
         win.on('windowSizeChange', this.sizeListener);
       } catch (err) {
         console.error('windowSizeChange subscription failed:', String(err));
       }
     }).catch((err: BusinessError) => {
       console.error(`getLastWindow failed: ${err.code} ${err.message}`);
     });
   }
   
   // Unregister the size change listener and release the reference to avoid memory leaks.
   aboutToDisappear(): void {
     if (this.mainWindow && this.sizeListener) {
       try {
         this.mainWindow.off('windowSizeChange', this.sizeListener);   // Unregister the listener.
       } catch (err) {
         console.warn('windowSizeChange unsubscribe failed:', String(err));
       }
     }
     this.mainWindow = null;   // Release the main window reference.
     this.sizeListener = null; // Release the listener callback reference.
   }
   ```

4. Make window content respond to window size changes.

   With a fixed size, window content cannot adapt to the window size: a small window is truncated and a large screen leaves blank space. You can set the content area width using a percentage (`'100%'`) and use [layoutWeight](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#layoutweight) to fill the remaining space, so that the content is fully displayed at any window size, leaving no blank space on large screens and no truncation in small windows.

   <!-- @[contentLayout](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowFreeformResize/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Content area: use percentage + layoutWeight to fill the remaining space so that it is fully displayed at any window size.
   Column({ space: 8 }) {
     Text('Window preview').fontSize(64)
     Text('Drag the window border or corner to experience free resize').fontSize(12).fontColor('#888')
   }
   .width('100%')
   .layoutWeight(1)
   .justifyContent(FlexAlign.Center)
   .backgroundColor('#E3F2FD')
   .borderRadius(12)
   ```