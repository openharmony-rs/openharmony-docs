# Window Adaptive Layout Development Practice (PC/2-in-1 Device)

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @wxcHello-->
<!--Designer: @ALTNAT-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=409f62d84ee58505e025b06d366354874a93b984 translatedAt=2026-11-12T04:52:02.053Z pushedAt=2026-11-12T07:45:42.147Z nl=1 -->

## When to Use

Applications face scenarios such as freeform window resizing, split screen, cross-screen, and screen rotation, where the window size changes continuously with user operations and screen state. The same content may be truncated, leave excessive whitespace, or become misaligned under different sizes such as full screen, split screen, and small windows. Window adaptive layout lets content automatically adjust its layout with window size, so that it is laid out reasonably at any size.

This document provides the following capability guidance and development ideas:

- The window width and height are reflected to the UI in real time as the window size changes.
- The window layout automatically adjusts the grid column count with the window width, and the content reflows reasonably.
- The window content automatically avoids avoid areas such as the status bar and navigation bar.

> **NOTE**
>
> The free-form window resizing scenario mainly applies to PC/2in1 devices. It also applies to other devices (some Phone and Tablet devices) that support and are in the [free-form window](freeform-window-overview.md#freeform-window) state.

## How to Develop

1. Declare support for free-form windows.

   In the [module.json5](../quick-start/module-configuration-file.md) configuration file, declare `"floating"` in the `supportWindowMode` attribute under the [abilities tag](../quick-start/module-configuration-file.md#abilities) so that the window supports continuous drag-and-drop resizing in the free-form window state.

   ``` json5
   "supportWindowMode": [
     "fullscreen",
     "split",
     "floating"
   ]
   ```

2. Obtain the main window through [getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9), continuously listen for window size changes, and obtain the window width in real time.

   Both the initialization and the window size change callback call the encapsulated `applyWidth()` in the example, which converts the window width to breakpoints. The breakpoints then determine the column count of the grid ([Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md)), letting content reflow automatically with window width. For the conversion logic, see step 3. When the page is destroyed, unregister the listener through [off('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offwindowsizechange7) in `aboutToDisappear` to avoid memory leaks.

   > **NOTE**
   >
   > The unit returned by [on('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowsizechange7) is px. Before comparing with vp thresholds, convert the unit through [px2vp](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#px2vp12).

   <!-- @[getLastWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   aboutToAppear(): void {
     // The page obtains the main window by itself, without relying on any changes in EntryAbility.
     const ctx = this.getUIContext().getHostContext();
     if (!ctx) {
       // In non-real-device environments such as the previewer, the host context cannot be obtained, so onAreaChange drives the breakpoint instead.
       return;
     }
     window.getLastWindow(ctx).then((win: window.Window) => {
       this.mainWindow = win;   // Save the main window instance.
   
       // Initialize once with the current window width, convert it to a breakpoint, and sync the UI.
       try {
         this.applyWidth(this.getUIContext().px2vp(win.getWindowProperties().windowRect.width));
       } catch (err) {
         console.error('Failed to get initial window width:', JSON.stringify(err));
       }
   
       // ...
   
       // The callback unit is px and needs to be converted to vp.
       this.onResize = (size: window.Size): void => {
         this.applyWidth(this.getUIContext().px2vp(size.width));
       };
       try {
         win.on('windowSizeChange', this.onResize);
       } catch (err) {
         console.error('Failed to subscribe to windowSizeChange:', String(err));
       }
   
       // ...
     }).catch((err: BusinessError) => {
       console.error(`getLastWindow failed: ${err.code} ${err.message}`);
     });
   }
   
   aboutToDisappear(): void {
     // Must unbind; otherwise, repeatedly entering and leaving the page registers the callback multiple times, causing memory leaks and multiple callbacks.
     if (this.mainWindow) {
       try {
         if (this.onResize) {
           this.mainWindow.off('windowSizeChange', this.onResize);
         }
         // ...
       } catch (err) {
         console.warn('Unsubscribe failed:', String(err));
       }
     }
     this.mainWindow = null;
     this.onResize = null;
     // ...
   }
   ```

3. Convert the window width to breakpoints, and then let the breakpoints determine the grid column count, so that content reflows automatically with window width.

   The breakpoint thresholds follow the common "xs/sm/md/lg/xl" division recommended by [grid layout](../ui/arkts-layout-development-grid-layout.md#breakpoints), covering common device widths: first convert the window width to a breakpoint and store it in a state variable decorated by [@State](../ui/state-management/arkts-state.md), then map the grid column count based on the breakpoint, and let this breakpoint state variable drive the column count of the Grid. When the breakpoint changes, the ArkTS declarative UI automatically re-renders, and the Grid column count updates accordingly. Combined with the [animation](../reference/apis-arkui/arkui-ts/ts-animatorproperty.md#animation) implicit animation, the content reflows smoothly when columns change. The number of columns corresponding to each breakpoint can be adjusted according to the business; the example uses 1 to 3 columns.

   Breakpoint definitions:

   | Breakpoint | Width range (vp) |
   |------|-------------|
   | xs | < 320 |
   | sm | [320, 600) |
   | md | [600, 840) |
   | lg | [840, 1440) |
   | xl | >= 1440 |

   <!-- @[breakpointGrid](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Convert the width (vp) to a breakpoint.
   private calcBreakpoint(widthVp: number): Breakpoint {
     if (widthVp < 320) {
       return Breakpoint.XS;
     }
     if (widthVp < 600) {
       return Breakpoint.SM;
     }
     if (widthVp < 840) {
       return Breakpoint.MD;
     }
     if (widthVp < 1440) {
       return Breakpoint.LG;
     }
     return Breakpoint.XL;
   }
   
   // Unified entry: after obtaining the width (vp), update both the width display and the breakpoint (single source of truth).
   private applyWidth(widthVp: number): void {
     this.windowWidth = Math.round(widthVp);
     this.currentBp = this.calcBreakpoint(widthVp);
   }
   
   // Convert the breakpoint to a label string for display in the information bar.
   private bpLabel(bp: Breakpoint): string {
     return ['XS', 'SM', 'MD', 'LG', 'XL'][bp];
   }
   
   // Determine the grid column count based on the breakpoint (driving both the information display and Grid.columnsTemplate, single source of truth).
   private getColumns(bp: Breakpoint): number {
     if (bp <= Breakpoint.SM) {
       return 1;
     }
     if (bp === Breakpoint.MD) {
       return 2;
     }
     return 3;
   }
   // ...
       // Adaptive grid: the column count is driven by the single source of truth currentBp. Grid + .animation() makes cards reflow smoothly when columns change.
       Grid() {
         ForEach([1, 2, 3, 4, 5, 6], (item: number) => {
           GridItem() {
             Column() {
               Text(`Card ${item}`)
                 .fontSize(18)
                 .fontWeight(FontWeight.Medium)
             }
             .width('100%')
             .height(100)
             .backgroundColor('#E3F2FD')
             .borderRadius(12)
             .justifyContent(FlexAlign.Center)
           }
         }, (item: number) => item.toString())
       }
       .columnsTemplate('1fr '.repeat(this.getColumns(this.currentBp)))
       .columnsGap(12)
       .rowsGap(12)
       .width('100%')
       .layoutWeight(1)
       // Smooth animation of card positions when columns change: .animation implicit animation.
       .animation({ duration: 300, curve: Curve.Smooth })
   ```

4. Obtain and sense avoid area changes, and dynamically adjust the padding of the window content.

   In modes such as full screen and free-floating windows, the system status bar and navigation bar may float above the window and obscure the content. The area occupied by these system bars is called the avoid area. The application reads the avoid area height of the status bar and navigation bar, and includes it in the content padding, so that the content shrinks outside the system bars. This is handled in three steps: read the avoid area, listen for avoid area changes, and apply the avoid area.

   Read the avoid area: [getWindowAvoidArea()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9) returns the avoid area height (px), which is converted to vp through `px2vp()` and stored in a state variable. The title bar height in the free-form window state can also be read through [getWindowDecorHeight()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowdecorheight11).

   <!-- @[avoidArea](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // The unit is px and needs to be converted to vp.
   private readAvoidArea(win: window.Window): void {
     try {
       const area: window.AvoidArea = win.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
       this.safeTop = Math.round(this.getUIContext().px2vp(area.topRect.height));
       this.safeBottom = Math.round(this.getUIContext().px2vp(area.bottomRect.height));
     } catch (err) {
       console.error('Could not read system avoid areas:', String(err));
     }
   }
   
   // Note: this API returns vp, while other APIs such as avoid area and rectangle return px.
   private readDecorHeight(win: window.Window): void {
     try {
       this.decorHeight = win.getWindowDecorHeight();
     } catch (err) {
       console.warn('Could not get title bar height:', String(err));
     }
   }
   ```

   Listen for avoid area changes: the [on('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onavoidareachange9) callback directly returns the latest avoid area data. When the page is destroyed, unregister it through [off('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offavoidareachange9) to avoid memory leaks.

   <!-- @[avoidAreaListener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   aboutToAppear(): void {
     // ...
       // Avoid area change: the data returned by the callback is always the latest, avoiding actively calling getWindowAvoidArea in windowSizeChange.
       this.onAvoidChange = (opts: window.AvoidAreaOptions): void => {
         this.safeTop = Math.round(this.getUIContext().px2vp(opts.area.topRect.height));
         this.safeBottom = Math.round(this.getUIContext().px2vp(opts.area.bottomRect.height));
       };
       try {
         win.on('avoidAreaChange', this.onAvoidChange);
       } catch (err) {
         console.error('avoidAreaChange subscription failed:', JSON.stringify(err));
       }
     }).catch((err: BusinessError) => {
       console.error(`getLastWindow failed: ${err.code} ${err.message}`);
     });
   }
   
   aboutToDisappear(): void {
     // Must unbind; otherwise, repeatedly entering and leaving the page registers the callback multiple times, causing memory leaks and multiple callbacks.
     if (this.mainWindow) {
       try {
         // ...
         if (this.onAvoidChange) {
           this.mainWindow.off('avoidAreaChange', this.onAvoidChange);
         }
       } catch (err) {
         console.warn('Unsubscribe failed:', String(err));
       }
     }
     // ...
     this.onAvoidChange = null;
   }
   ```

   Apply the avoid area: add `safeTop` to the top of the content padding and `safeBottom` to the bottom. The title bar differs from the avoid area: when using percentage or flex layout, the system has already placed the content into the drawable area (automatically excluding the title bar), so the title bar does not need to be handled by the application in this scenario. Only when absolute positioning is performed based on the window rectangle (`windowRect`, including the title bar) is it necessary to use the drawable area (`drawableRect`) to position the content and avoid the title bar.

   <!-- @[avoidAreaPadding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   Column({ space: 16 }) {
     // ...
   }
   .width('100%')
   .height('100%')
   // The content padding dynamically adjusts with the system avoid area.
   .padding({
     left: 16,
     right: 16,
     top: 16 + this.safeTop,
     bottom: 16 + this.safeBottom
   })
   ```