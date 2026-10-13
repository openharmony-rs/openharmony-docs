# 窗口生命周期实践案例

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

窗口生命周期提供了丰富的事件监听和状态管理能力，可以支持应用在PC/2in1、Tablet等多种设备形态下适配窗口的前后台切换。

开发者在开发应用时，要兼顾应用的生命周期在多种设备类型上的体验，为了帮助开发者快速上手，针对如下典型场景提供适配示例。

## PC应用主窗恢复

在PC/2in1设备上，应用主窗口最小化后，可通过调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口将主窗口从最小化状态恢复到前台显示，并恢复到进入最小化状态之前的大小和位置。若主窗口已处于前台状态，调用该接口仅抬升主窗口层级。

与Phone等设备不同，PC/2in1设备上窗口最小化后**不会**驱动UIAbility进入后台状态，UIAbility始终处于前台状态（onForeground）。因此，恢复窗口时无需重新启动UIAbility，窗口能够快速恢复到最小化前的显示状态。

> **说明：**
>
> - [minimize()](../reference/apis-arkui/arkts-apis-window-Window.md#minimize11)和[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口仅在PC/2in1设备、Tablet设备的[电脑模式](window-terminology.md#pc-mode电脑模式)下可正常调用，在其他设备和其他模式下调用会返回801错误码。
>
> - 不同设备窗口进入后台状态与UIAbility生命周期的关系，请参考[不同设备UIAbility生命周期的差异化行为](window-lifecycle.md#不同设备UIAbility生命周期的差异化行为)。

调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口前，需通过[WindowStage](../reference/apis-arkui/arkts-apis-window-WindowStage.md)的[getMainWindowSync()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#getmainwindowsync9)接口获取应用主窗口实例，再通过此实例调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口恢复主窗口。

示例代码如下：

<!-- @[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowRestoreSample/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  mainWindow: window.Window | undefined;

  aboutToAppear() {
    // 在 EntryAbility.ets 中通过 windowStage.getMainWindowSync() 保存主窗
    this.mainWindow = AppStorage.get('mainWindow_Restore') as window.Window;
  }

  minimizeAndRestore() {
    if (!this.mainWindow) {
      console.error('Main window is not available.');
      return;
    }
    try {
      // 调用minimize()接口，使主窗最小化
      this.mainWindow.minimize();
      // 设置延时函数，延时5秒钟后对主窗进行恢复
      setTimeout(() => {
        // 调用restore()接口，将主窗口从最小化状态恢复到前台显示
        this.mainWindow?.restore().then(() => {
          console.info('Succeeded in restoring the window.');
        }).catch((err: BusinessError) => {
          console.error(`Failed to restore the window. Code is ${err.code}, message is ${err.message}`);
        });
      }, 5000);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      console.error(`Failed to minimize and restore the window. Code is ${err.code}, message is ${err.message}`);
    }
  }

  build() {
    Column() {
      Text('Minimize and auto restore')
        .fontSize(17)
      Button('Minimize and restore')
        .onClick(() => {
          console.info('Click: Minimize and restore');
          this.minimizeAndRestore();
        })
        .margin({ top: 20 })
    }
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
    .height('100%')
    .width('100%')
  }
}
```
