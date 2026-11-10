# 窗口自由缩放开发实践案例 (PC/2in1)

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @wxcHello-->
<!--Designer: @ALTNAT-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->

## 场景介绍

**窗口自由缩放**是应用在[自由窗口](freeform-window-overview.md#自由窗口)状态下，拖拽窗口连续调整窗口大小，以便在同一屏幕上灵活排布多个窗口，而不是在几个固定的尺寸之间变动调节。

窗口尺寸连续变化对应用提出了额外要求：内容需要在任意尺寸下正确显示，尺寸限制需要合理，界面需要实时跟随。本案例覆盖以下内容：

- 窗口在被拖拽缩放过程中，应用能实时感知窗口尺寸变化，并将宽高刷新到界面。
- 为窗口缩放设置合理的尺寸范围，避免缩放过小导致内容截断、过大导致空间浪费。
- 窗口内容随窗口尺寸连续响应。

> **说明：**
>
> 窗口自由缩放场景主要适用于PC/2in1设备，对于支持并处于自由窗口状态的其他设备（部分Phone、Tablet设备）同样适用。

## 开发步骤

1. 声明支持自由窗口。

   在[module.json5](../quick-start/module-configuration-file.md)配置文件中[abilities标签](../quick-start/module-configuration-file.md#abilities标签)下的supportWindowMode属性声明"floating"，使窗口支持自由窗口下的连续拖拽缩放。

   ``` json5
   "supportWindowMode": [
     "fullscreen",
     "split",
     "floating"
   ]
   ```

2. 获取主窗口并完成初始化。

   通过[getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1)获取主窗口，并完成相关初始化操作（此例中由封装的setupWindow()方法完成）。主要包括以下操作：

   - 使能拖拽缩放：拖拽缩放是自由窗口的固有能力，是否允许用户拖拽则由[setResizeByDragEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setresizebydragenabled14-1)开关决定。该开关的默认状态不保证开启，示例显式开启，确保进入页面即可拖拽缩放。
   - 设置尺寸范围：窗口被缩放过小或过大时，会导致内容截断、布局错乱或空间浪费。可通过[setWindowLimits()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowlimits11)接口设置尺寸范围，该范围会与系统限制取交集，生效值可能比入参更保守。
   - 同步初始尺寸：此例中通过applySize()将窗口当前宽高同步到界面。

   <!-- @[init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowFreeformResize/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 把窗口宽高（px）写回状态变量，驱动界面刷新
   private applySize(widthPx: number, heightPx: number): void {
     this.winWidthPx = Math.round(widthPx);
     this.winHeightPx = Math.round(heightPx);
   }

   // 读取生效尺寸范围（入参与系统限制的交集），存到状态变量供界面展示
   private readLimits(win: window.Window): void {
     try {
       const l: window.WindowLimits = win.getWindowLimitsVP();   // 返回单位vp
       // 把生效范围分别存到状态变量
       this.limitsMinW = l.minWidth ?? 0;
       this.limitsMaxW = l.maxWidth ?? 0;
       this.limitsMinH = l.minHeight ?? 0;
       this.limitsMaxH = l.maxHeight ?? 0;
       console.info(`Effective range: ${l.minWidth}~${l.maxWidth} × ${l.minHeight}~${l.maxHeight}`);
     } catch (err) {
       console.error('Failed to read effective size range:', String(err));
     }
   }

   // 窗口初始化：使能拖拽缩放、设置尺寸范围、同步初始尺寸
   private setupWindow(win: window.Window): void {
     // 默认已支持拖拽缩放，显式开启以防被关闭
     win.setResizeByDragEnabled(true).then(() => {
       console.info('Drag-to-resize enabled');
     }).catch((err: BusinessError) => {
       console.error(`setResizeByDragEnabled failed: ${err.code} ${err.message}`);
     });

     // 防止过度缩放导致内容截断或布局错乱
     const limits: window.WindowLimits = {
       minWidth: 480,
       minHeight: 360,
       maxWidth: 1600,
       maxHeight: 1000,
       pixelUnit: window.PixelUnit.VP
     };
     win.setWindowLimits(limits).then(() => {
       this.readLimits(win);   // 读取“入参与系统限制的交集”，并打印生效范围
     }).catch((err: BusinessError) => {
       console.error(`setWindowLimits failed: ${err.code} ${err.message}`);
     });

     // 读取初始窗口尺寸，同步到界面
     try {
       this.applySize(win.getWindowProperties().windowRect.width,
         win.getWindowProperties().windowRect.height);
     } catch (err) {
       console.error('Failed to get initial window size:', JSON.stringify(err));
     }
   }

   // 获取主窗口、完成初始化，并注册尺寸变化监听
   aboutToAppear(): void {
     const ctx = this.getUIContext().getHostContext();   // 获取宿主上下文作为getLastWindow入参
     if (!ctx) {
       return;   // 预览器等环境拿不到宿主上下文，本示例依赖真实窗口，直接跳过
     }
     window.getLastWindow(ctx).then((win: window.Window) => {
       this.mainWindow = win;   // 保存主窗口实例
       this.setupWindow(win);   // 完成初始化：使能拖拽缩放、设置尺寸范围、同步初始尺寸

       // ...
     }).catch((err: BusinessError) => {
       console.error(`getLastWindow failed: ${err.code} ${err.message}`);
     });
   }

   // ...
   ```

3. 监听窗口尺寸变化，实时更新窗口宽高。

   通过[on('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowsizechange7)监听窗口尺寸变化，窗口拖动或拖拽缩放后系统回调监听函数，在回调中将窗口宽高（px）经applySize()写回状态变量，并实现窗口宽高的实时刷新。

   页面销毁时需在aboutToDisappear里通过[off('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offwindowsizechange7)注销监听，避免内存泄漏。

   <!-- @[resizeChange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowFreeformResize/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取主窗口、完成初始化，并注册尺寸变化监听
   aboutToAppear(): void {
     // ...
   
       // 尺寸变化回调：把新宽高写回状态变量，驱动界面刷新
       this.sizeListener = (size: window.Size): void => {
         this.applySize(size.width, size.height);
       };
       // 注册监听，窗口拖动/拖拽缩放后回调sizeListener
       try {
         win.on('windowSizeChange', this.sizeListener);
       } catch (err) {
         console.error('windowSizeChange subscription failed:', String(err));
       }
     }).catch((err: BusinessError) => {
       console.error(`getLastWindow failed: ${err.code} ${err.message}`);
     });
   }
   
   // 注销尺寸变化监听并释放引用，避免内存泄漏
   aboutToDisappear(): void {
     if (this.mainWindow && this.sizeListener) {
       try {
         this.mainWindow.off('windowSizeChange', this.sizeListener);   // 注销监听
       } catch (err) {
         console.warn('windowSizeChange unsubscribe failed:', String(err));
       }
     }
     this.mainWindow = null;   // 释放主窗口引用
     this.sizeListener = null; // 释放监听回调引用
   }
   ```

4. 窗口内容随窗口尺寸响应变化。

   使用固定尺寸时，窗口内容无法随窗口尺寸自适应，小窗会被截断、大屏会留白。可以通过使用百分比（'100%'）设置内容区宽度，并用[layoutWeight](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#layoutweight)铺满剩余空间，实现窗口任意尺寸下内容完整显示，做到大屏不留白、小窗不截断。

   <!-- @[contentLayout](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowFreeformResize/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 内容区：百分比 + layoutWeight铺满剩余空间，任意窗口尺寸下都完整显示
   Column({ space: 8 }) {
     Text('窗口预览').fontSize(64)
     Text('拖动窗口边框或角，体验自由缩放').fontSize(12).fontColor('#888')
   }
   .width('100%')
   .layoutWeight(1)
   .justifyContent(FlexAlign.Center)
   .backgroundColor('#E3F2FD')
   .borderRadius(12)
   ```