# 窗口生命周期实践案例

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

窗口生命周期提供了丰富的事件监听和状态管理能力，可以支持应用在PC/2in1、Tablet等多种设备形态下适配窗口的前后台切换。

开发者在开发应用时，要兼顾应用的生命周期在多种设备类型上的体验，为了帮助开发者快速上手，针对如下典型场景提供适配示例。

## PC应用从托盘区恢复主窗

在PC/2in1设备上，可通过DeskTopExtensionKit提供的[statusBarManager](../reference/apis-ability-kit/js-apis-app-ability-statusBarManager.md)接口将应用图标注册到状态栏托盘区，并监听托盘图标的点击事件。应用主窗口进入后台状态后，当用户点击托盘图标时，应用可调用[restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口将主窗口恢复到前台显示，并恢复到进入后台状态之前的大小和位置。

> **说明：**
>
> - [restore()](../reference/apis-arkui/arkts-apis-window-Window.md#restore14)接口仅在PC/2in1设备、Tablet设备的[电脑模式](window-terminology.md#pc-mode电脑模式)下可正常调用，在其他设备和其他模式下调用会返回801错误码。
>
> - 不同设备窗口进入后台状态与UIAbility生命周期的关系，请参考[不同设备UIAbility生命周期的差异化行为](window-lifecycle.md#不同设备UIAbility生命周期的差异化行为)。

示例代码如下：

<!-- @[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowRestoreSample/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError, emitter } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { statusBarManager } from '@kit.DeskTopExtensionKit';
import { image } from '@kit.ImageKit';
import { window } from '@kit.ArkUI';

const DOMAIN: number = 0xFF00;
const TAG: string = '[Sample_WindowRestore]';
// 默认弹窗高度，单位vp
const QUICK_OPERATION_HEIGHT: number = 300;

@Entry
@Component
struct Index {
  private mainWindow: window.Window | undefined;

  aboutToAppear() {
    this.mainWindow = AppStorage.get('mainWindow_Restore') as window.Window;
    if (!this.mainWindow) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'Failed to get main window from AppStorage.');
      return;
    }
    const context = this.getUIContext().getHostContext() as common.Context;
    if (!context) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'Failed to get host context.');
      return;
    }
    this.addToStatusBar(context);
  }

  onStatusBarIconClick = (eventData: emitter.EventData) => {
    // 自定义图标点击业务
    const data = eventData.data;
    if (data) {
      switch (data['iconClickType']) {
        case 'leftClick':
          this.restoreMainWindow();
          break;
        default:
          break;
      }
    }
  }

  async addToStatusBar(context: common.Context): Promise<void> {
    // 使用应用默认图标作为托盘图标
    const iconData = await context.resourceManager.getMediaContent($r('app.media.foreground'));
    const imageSource = image.createImageSource(iconData.buffer);
    const pixelMap: image.PixelMap = await imageSource.createPixelMap();
    const icon: statusBarManager.StatusBarIcon = {
      white: pixelMap,
      black: pixelMap
    };

    // 构建左键业务弹窗信息。abilityName传空字符串时，支持通过监听statusBarIconClick事件处理点击业务
    const operation: statusBarManager.QuickOperation = {
      abilityName: '',
      title: 'Demo',
      height: QUICK_OPERATION_HEIGHT
    };

    // 构建添加到状态栏的图标详细信息
    const item: statusBarManager.StatusBarItem = {
      icons: icon,
      quickOperation: operation
    };

    try {
      statusBarManager.addToStatusBar(context, item);
      statusBarManager.on('statusBarIconClick', this.onStatusBarIconClick);
      hilog.info(DOMAIN, TAG, '%{public}s', 'Succeeded in adding icon to status bar.');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, 'Failed to add icon to status bar. Code: %{public}s, message: %{public}s',
        `${err.code}`, `${err.message}`);
    }
  }

  minimizeMainWindow() {
    if (!this.mainWindow) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'Failed to minimize the window. Main window is not available.');
      return;
    }
    try {
      this.mainWindow.minimize();
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, 'Failed to minimize the window. Code: %{public}s, message: %{public}s',
        `${err.code}`, `${err.message}`);
    }
  }

  restoreMainWindow() {
    if (!this.mainWindow) {
      hilog.error(DOMAIN, TAG, '%{public}s', 'Failed to restore the window. Main window is not available.');
      return;
    }
    try {
      // 调用restore()接口，将主窗口从最小化状态恢复到前台显示
      this.mainWindow.restore().then(() => {
        hilog.info(DOMAIN, TAG, '%{public}s', 'Succeeded in restoring the window.');
      }).catch((err: BusinessError) => {
        hilog.error(DOMAIN, TAG, 'Failed to restore the window. Code: %{public}s, message: %{public}s',
          `${err.code}`, `${err.message}`);
      });
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      hilog.error(DOMAIN, TAG, 'Failed to restore the window. Code: %{public}s, message: %{public}s',
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
          this.minimizeMainWindow();
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
