# 窗口生命周期实践案例

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

窗口生命周期提供了丰富的事件监听和状态管理能力，可以支持应用在PC/2in1、Tablet等多种设备形态下适配窗口的前后台切换。

开发者在开发应用时，要兼顾应用的生命周期在多种设备类型上的体验，为了帮助开发者快速上手，针对如下典型场景提供适配示例。

## PC设备应用从后台恢复至前台

在PC/2in1设备上，应用主窗口进入后台状态后，可通过调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口将主窗口恢复到前台显示，并恢复到进入后台状态之前的大小和位置。若主窗口已处于前台状态，调用该接口仅抬升主窗口层级。

对于已将应用图标添加到状态栏的应用，可通过监听状态栏图标点击事件，在用户点击状态栏图标时调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口恢复应用主窗口。应用如何接入状态栏请参考[应用接入状态栏](https://developer.huawei.com/consumer/cn/doc/doccenter-capabilities/statusbar-extension-guide)

> **说明：**
>
> - [restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口仅在PC/2in1设备、Tablet设备的[电脑模式](window-terminology.md#pc-mode电脑模式)下可正常调用，在其他设备和其他模式下调用会返回801错误码。
>
> - 不同设备窗口进入后台状态与UIAbility生命周期的关系，请参考[不同设备UIAbility生命周期的差异化行为](window-lifecycle.md#不同设备UIAbility生命周期的差异化行为)。

示例代码如下：

<!-- @[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowRestoreSample/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import hilog from '@ohos.hilog';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_WindowRestore]';

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
      hilog.error(DOMAIN, TAG, '%{public}s', 'Main window is not available.');
      return;
    }
    try {
      // 调用minimize()接口，使主窗进入后台状态
      this.mainWindow.minimize();
      // 设置延时函数，延时5秒钟后对主窗进行恢复
      setTimeout(() => {
        // 调用restore()接口，将主窗口恢复到前台显示
        this.mainWindow?.restore().then(() => {
          hilog.info(DOMAIN, TAG, '%{public}s', 'Succeeded in restoring the window.');
        }).catch((err: BusinessError) => {
          hilog.error(DOMAIN, TAG, 'Failed to restore the window. Code: %{public}s, message: %{public}s',
            `${err.code}`, `${err.message}`);
        });
      }, 5000);
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, 'Failed to minimize and restore the window. Code: %{public}s, message: %{public}s',
        `${err.code}`, `${err.message}`);
    }
  }

  build() {
    Column() {
      Text($r('app.string.minimize_text'))
        .id('minimizeText')
        .fontSize(17)
      Button($r('app.string.minimize_button'))
        .id('minimizeButton')
        .onClick(() => {
          hilog.info(DOMAIN, TAG, '%{public}s', 'Click: Minimize and restore');
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
