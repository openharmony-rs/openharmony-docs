# 窗口自适应布局开发实践案例 (PC/2in1)

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @wxcHello-->
<!--Designer: @ALTNAT-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->

## 场景介绍

应用会面临窗口自由缩放、分屏、跨屏、屏幕旋转等场景，窗口尺寸随用户操作和屏幕状态持续变化。同样的内容在全屏、分屏、小窗等不同尺寸下可能被截断、留白过多或布局错乱。窗口自适应布局就是让内容随窗口尺寸自动调整布局，在任意尺寸下都合理布局。

本文提供以下能力指导与开发思路：

- 窗口宽高随窗口尺寸变化实时反映到界面。
- 窗口布局随窗口宽度自动调整栅格列数，内容合理重排。
- 窗口内容自动避开状态栏、导航栏等避让区。

> **说明：**
>
> 窗口自由缩放场景主要适用于PC/2in1设备，对于支持并处于[自由窗口](freeform-window-overview.md#自由窗口)状态的其他设备（部分Phone、Tablet设备）同样适用。

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

2. 通过[getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9)获取主窗口，持续监听窗口尺寸变化，实时获取窗口宽度。

   初始化与窗口尺寸变化回调都调用示例封装的applyWidth()，把窗口宽度换算成断点，断点再决定栅格（[Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md)）列数，让内容随窗口宽度自动重排，换算逻辑见步骤3。页面销毁时需在aboutToDisappear里通过[off('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offwindowsizechange7)注销监听，避免内存泄漏。

   > **说明：**
   >
   > [on('windowSizeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onwindowsizechange7)返回单位是px，当与vp阈值比较前，需先通过[px2vp](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#px2vp12)转换单位。

   <!-- @[getLastWindow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   aboutToAppear(): void {
     // 页面自包含获取主窗口：不依赖EntryAbility做任何改动。
     const ctx = this.getUIContext().getHostContext();
     if (!ctx) {
       // 预览器等非真机环境拿不到宿主上下文，改由onAreaChange驱动断点
       return;
     }
     window.getLastWindow(ctx).then((win: window.Window) => {
       this.mainWindow = win;   // 保存主窗口实例

       // 用当前窗口宽度做一次初始化，换算断点并同步界面
       try {
         this.applyWidth(this.getUIContext().px2vp(win.getWindowProperties().windowRect.width));
       } catch (err) {
         console.error('Failed to get initial window width:', JSON.stringify(err));
       }

       // ...

       // 回调单位是px，需转vp
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
     // 必须解绑，否则页面反复进出会重复注册回调，造成内存泄漏与多次回调
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

3. 把窗口宽度换算成断点，再由断点决定栅格列数，让内容随窗口宽度自动重排。

   断点阈值沿用[栅格布局](../ui/arkts-layout-development-grid-layout.md#栅格容器断点)推荐的"xs/sm/md/lg/xl"通用划分，覆盖常见设备宽度：先把窗口宽度换算成断点存进[@State](../ui/state-management/arkts-state.md)装饰的状态变量，再根据断点映射出栅格列数，由该断点状态变量驱动Grid的列数。断点变化时，ArkTS声明式UI会自动重渲染，Grid列数随之更新，配合[animation](../reference/apis-arkui/arkui-ts/ts-animatorproperty.md#animation)隐式动画让换列时内容平滑重排。各断点对应几列可按业务调整，示例采用1至3列。

   断点定义：

   | 断点 | 宽度范围 (vp) |
   |------|-------------|
   | xs | < 320 |
   | sm | [320, 600) |
   | md | [600, 840) |
   | lg | [840, 1440) |
   | xl | >= 1440 |

   <!-- @[breakpointGrid](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 把宽度（vp）换算成断点
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

   // 统一入口：拿到宽度（vp）后同时更新宽度显示与断点（单一数据源）
   private applyWidth(widthVp: number): void {
     this.windowWidth = Math.round(widthVp);
     this.currentBp = this.calcBreakpoint(widthVp);
   }

   // 断点转标签字符串，用于信息条展示
   private bpLabel(bp: Breakpoint): string {
     return ['XS', 'SM', 'MD', 'LG', 'XL'][bp];
   }

   // 根据断点决定栅格列数（同时驱动信息展示与Grid.columnsTemplate，单一数据源）
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
       // 自适应栅格：列数由currentBp单一数据源驱动，Grid + .animation()让换列时卡片平滑重排
       Grid() {
         ForEach([1, 2, 3, 4, 5, 6], (item: number) => {
           GridItem() {
             Column() {
               Text(`卡片 ${item}`)
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
       // 换列时卡片位置平滑动画：.animation隐式动画
       .animation({ duration: 300, curve: Curve.Smooth })
   ```

4. 获取并感知避让区变化，动态调整窗口内容的边距（padding）。

   全屏、自由悬浮窗口等模式下，系统状态栏、导航栏可能悬浮在窗口上方遮挡内容，这些系统栏占用的区域称为避让区（avoid area）。应用读取状态栏、导航栏的避让区高度，计入内容内边距（padding），使内容收缩到系统栏之外，分三步处理：读取避让区、监听避让区变化和应用避让区。

   读取避让区：[getWindowAvoidArea()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowavoidarea9)返回避让区高度（px），经px2vp()转vp后存入状态变量；自由窗口状态下的标题栏高度可由[getWindowDecorHeight()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowdecorheight11)一并读取。

   <!-- @[avoidArea](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 单位px，需转vp
   private readAvoidArea(win: window.Window): void {
     try {
       const area: window.AvoidArea = win.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
       this.safeTop = Math.round(this.getUIContext().px2vp(area.topRect.height));
       this.safeBottom = Math.round(this.getUIContext().px2vp(area.bottomRect.height));
     } catch (err) {
       console.error('Could not read system avoid areas:', String(err));
     }
   }

   // 注意：该接口返回vp，避让区/矩形等其它接口返回px
   private readDecorHeight(win: window.Window): void {
     try {
       this.decorHeight = win.getWindowDecorHeight();
     } catch (err) {
       console.warn('Could not get title bar height:', String(err));
     }
   }
   ```

   监听避让区变化：[on('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onavoidareachange9)回调直接返回最新避让区数据，页面销毁时用[off('avoidAreaChange')](../reference/apis-arkui/arkts-apis-window-Window.md#offavoidareachange9)注销避免内存泄漏。

   <!-- @[avoidAreaListener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   aboutToAppear(): void {
     // ...
       // 避让区变化：回调返回的数据总是最新，避免在windowSizeChange里主动getWindowAvoidArea
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
     // 必须解绑，否则页面反复进出会重复注册回调，造成内存泄漏与多次回调
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

   应用避让区：在内容padding顶部加safeTop，底部加safeBottom。标题栏与避让区不同：使用百分比或flex布局时，系统已把内容排进可绘制区（自动排除标题栏），此场景下标题栏无需应用处理；只有以窗口矩形（windowRect，含标题栏）做绝对定位时，才需改用可绘制区域（drawableRect）定位内容，避开标题栏。

   <!-- @[avoidAreaPadding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/WindowAdaptive/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   Column({ space: 16 }) {
     // ...
   }
   .width('100%')
   .height('100%')
   // 内容padding随系统避让区动态调整
   .padding({
     left: 16,
     right: 16,
     top: 16 + this.safeTop,
     bottom: 16 + this.safeBottom
   })
   ```