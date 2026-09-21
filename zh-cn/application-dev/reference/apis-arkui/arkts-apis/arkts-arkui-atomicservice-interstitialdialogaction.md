# @ohos.atomicservice.InterstitialDialogAction(This section describes the interfaces used by InterstitialDialogAction)

## 子组件

无。

## 属性

不支持[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)。

## 事件

不支持[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)。

## 导入模块

```TypeScript
import { InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [InterstitialDialogAction](arkts-arkui-atomicservice-interstitialdialogaction-interstitialdialogaction-c.md) | InterstitialDialogAction弹框在原子化服务中用于在保持当前的上下文环境时，临时展示用户需关注的信息或待处理的操作，用户点击弹框的不同区域可以触发对应的回调动作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DialogOptions](arkts-arkui-atomicservice-interstitialdialogaction-dialogoptions-i.md) | 设置弹框特有的属性以及提供给用户自定义的点击触发动作。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BottomOffset](arkts-arkui-atomicservice-interstitialdialogaction-bottomoffset-e.md) | 设置不同情景模式下弹框距离底部的距离，判断依据为是否存在菜单栏，默认显示为不存在菜单栏情况下的距离。 |
| [IconStyle](arkts-arkui-atomicservice-interstitialdialogaction-iconstyle-e.md) | 设置关闭按钮的色调样式，默认为亮色调。 |
| [TitlePosition](arkts-arkui-atomicservice-interstitialdialogaction-titleposition-e.md) | 设置主副标题之间的上下相对位置，默认设置为主标题在副标题之上。 |

## 示例

### 示例1

为可选属性设置相应值，用两种不同参数类型分别为主标题、副标题设置颜色值，关闭按钮设置为暗色调，主副标题相对位置设置为主标题在副标题上方，底部距离类型设置为不存在菜单栏情况下的距离。

```TypeScript
// ../entryability/EntryAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let dialogUIContext: UIContext | null = null;

export function getDialogUIContext(): UIContext | null {
  if (dialogUIContext === null) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'dialogUIContext is null');
  }
  return dialogUIContext;
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content, code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content.');
    });

    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      dialogUIContext = windowClass.getUIContext();
    });

    // 获取窗口
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      // 设置窗口非全屏
      windowClass.setWindowLayoutFullScreen(false);
    })
  }

  onWindowStageDestroy(): void {
    // Main window is destroyed, release UI related resources
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    // Ability has back to background
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```



```TypeScript
// Index.ets
import { getDialogUIContext } from '../entryability/EntryAbility';
import { UIContext, InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('show dialog')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let ctx: UIContext | null = getDialogUIContext();
            let interstitialDialogAction: InterstitialDialogAction = new InterstitialDialogAction({
              uiContext: ctx as UIContext,
              title: '主标题',
              subtitle: '副标题',
              titleColor: 'rgb(255, 192, 0)',
              subtitleColor: Color.Red,
              backgroundImage: $r('app.media.testBackgroundImg'),
              foregroundImage: $r('app.media.testForegroundImg'),
              iconStyle: IconStyle.DARK,
              titlePosition: TitlePosition.TOP,
              bottomOffsetType: BottomOffset.OFFSET_FOR_NONE,
              onDialogClick: () => { console.info('outer dialog click action') },
              onDialogClose: () => { console.info('outer close action') }
            });
            interstitialDialogAction.openDialog();
          })
      }
      .width('100%')
    }
    .height('100%')
    .backgroundColor('rgba(0, 0, 0, 0.1)')
  }
}
```

### 示例2

为可选属性设置相应值，用两种不同参数类型分别为主标题、副标题设置颜色值，关闭按钮设置为亮色调，主副标题相对位置设置为主标题在副标题下方，底部距离类型设置为存在菜单栏情况下的距离。

```TypeScript
// ../entryability/EntryAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let dialogUIContext: UIContext | null = null;

export function getDialogUIContext(): UIContext | null {
  if (dialogUIContext === null) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'dialogUIContext is null');
  }
  return dialogUIContext;
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content, code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content.');
    });

    let windowClass: window.Window | undefined = undefined;
    windowStage.getMainWindow((err: BusinessError, data) => {
      let errCode: number = err.code;
      if (errCode) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      dialogUIContext = windowClass.getUIContext();
    });

    // 获取窗口
    windowStage.getMainWindow((err, data) => {
      if (err.code) {
        console.error(`Failed to obtain the main window, code: ${err.code}, message: ${err.message}`);
        return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the main window. Data: ' + JSON.stringify(data));
      // 设置窗口非全屏
      windowClass.setWindowLayoutFullScreen(false);
    })
  }

  onWindowStageDestroy(): void {
    // Main window is destroyed, release UI related resources
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    // Ability has back to background
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```

```TypeScript
// Index.ets
import { getDialogUIContext } from '../entryability/EntryAbility';
import { UIContext, InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('show dialog')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let ctx: UIContext | null = getDialogUIContext();
            let interstitialDialogAction: InterstitialDialogAction = new InterstitialDialogAction({
              uiContext: ctx as UIContext,
              title: '主标题',
              subtitle: '副标题',
              titleColor: 'rgb(255, 192, 0)',
              subtitleColor: Color.Red,
              backgroundImage: $r('app.media.testBackgroundImg'),
              foregroundImage: $r('app.media.testForegroundImg'),
              iconStyle: IconStyle.LIGHT,
              titlePosition: TitlePosition.BOTTOM,
              bottomOffsetType: BottomOffset.OFFSET_FOR_BAR,
              onDialogClick: () => { console.info('outer dialog click action') },
              onDialogClose: () => { console.info('outer close action') }
            });
            interstitialDialogAction.openDialog();
          })
      }
      .width('100%')
    }
    .height('100%')
    .backgroundColor('rgba(0, 0, 0, 0.1)')
  }
}
```
