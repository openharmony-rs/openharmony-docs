# @ohos.arkui.advanced.FullScreenLaunchComponent(Defines the fullScreen launch component)

## 子组件

无。

## 属性

不支持[通用属性](../arkts-components/arkts-arkui-common-comp.md#common)。

## 事件

不支持[通用事件](../arkts-components/arkts-arkui-common-comp.md#common)。

## 导入模块

```TypeScript
import { FullScreenLaunchComponent } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [FullScreenLaunchComponent](arkts-arkui-arkui-advanced-fullscreenlaunchcomponent-fullscreenlaunchcomponent-s.md) | 全屏启动原子化服务组件，当提供方授权使用方嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。 |

## 示例

本示例展示组件使用方法和提供方原子化服务的实现。实际运行时请使用开发者自己的原子化服务appId。

FullScreenLaunchComponent组件需要由使用方调用。在提供方完成本地的安装后，即可在使用方应用或者原子化服务中全屏嵌入式拉起提供方的原子化服务。

> 说明：
> 
> 由于嵌入式原子化服务运行在独立进程，其崩溃异常不会直接暴露在宿主的日志中。本地调试时可通过以下方式查看真实报错栈：
> 
> 打开DevEco Studio的HiLog面板。
> 
> 将左上角的模式切换为User logs of selected app。
> 
> 在右侧进程列表中，选择被拉起的原子化服务进程（被拉起原子化服务的包名，且后缀带有embeddable字样）。

使用方

```TypeScript
// 使用方入口界面Index.ets内容如下：
import { FullScreenLaunchComponent } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State appId: string = '6917573653426122083'; // 原子化服务appId

  build() {
    Row() {
      Column() {
        FullScreenLaunchComponent({
          content: ColumnChild,
          appId: this.appId,
          options: {},
          onTerminated: (info) => {
            console.info(`onTerminated code: ${info.code.toString()}`);
          },
          onError: (err) => {
            console.error(`onError code: ${err.code}, message: ${err.message}`);
          },
          onReceive: (data) => {
            console.info(`onReceive, data: ${JSON.stringify(data)}`);
          }
        }).width('80vp').height('80vp')
      }
      .width('100%')
    }
    .height('100%')
  }
}

@Builder
function ColumnChild() {
  Column() {
    Image($r('app.media.startIcon'))
    Text('test')
  }
}
```

组件提供方

原子化服务提供方需要修改两个文件：

提供方入口文件：/src/main/ets/entryability/EntryAbility.ets。

```TypeScript
import { AbilityConstant, Want, EmbeddableUIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends EmbeddableUIAbility {
  storage = new LocalStorage();
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let mainWindow = windowStage.getMainWindowSync();
    this.storage.setOrCreate('window', mainWindow);
    this.storage.setOrCreate('windowStage', windowStage);
    windowStage.loadContent('pages/Index', this.storage);
  }

  onWindowStageDestroy(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```

提供方扩展Ability入口页面文件：/src/main/ets/pages/Index.ets。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();

  build() {
    Row() {
      Column() {
        GridRow({ columns: 2 }) {
          GridCol() {
            Button('setWindowSystemBar')
              .onClick(() => {
                this.testSetSystemBarEnable();
              }).width(120)
          }.height(60)

          GridCol() {
            Button('setGestureBack')
              .onClick(() => {
                this.testSetGestureBackEnable();
              }).width(120)
          }.height(60)

          GridCol() {
            Button('setImmersive')
              .onClick(() => {
                this.testSetImmersiveEnable();
              }).width(120)
          }.height(60)

          GridCol() {
            Button('setSpecificSystemBarEnabled')
              .onClick(() => {
                this.testSetSpecificSystemBarEnabled();
              }).width(120)
          }.height(60)
        }
      }
      .width('100%')
    }
    .height('100%')
  }

  testSetSystemBarEnable() {
    let window: window.Window | undefined = this.storage?.get('window');
    let promise = window?.setWindowSystemBarEnable(['status']);
    promise?.then(() => {
      console.info('setWindowSystemBarEnable success');
    }).catch((err: BusinessError) => {
      console.error(`setWindowSystemBarEnable failed, code: ${err.code}, message: ${err.message}`);
    });
  }

  testSetGestureBackEnable() {
    let window: window.Window | undefined = this.storage?.get('window');
    let promise = window?.setGestureBackEnabled(true);
    promise?.then(() => {
      console.info('setGestureBackEnabled success');
    }).catch((err: BusinessError) => {
      console.error(`setGestureBackEnabled failed, code: ${err.code}, message: ${err.message}`);
    });
  }

  testSetImmersiveEnable() {
    let window: window.Window | undefined = this.storage?.get('window');
    try {
      window?.setImmersiveModeEnabledState(true);
    } catch (err) {
      console.error(`setImmersiveModeEnabledState failed, code: ${err.code}, message: ${err.message}`);
    }
  }

  testSetSpecificSystemBarEnabled() {
    let window: window.Window | undefined = this.storage?.get('window');
    let promise = window?.setSpecificSystemBarEnabled('navigationIndicator', false, false);
    promise?.then(() => {
      console.info('setSpecificSystemBarEnabled success');
    }).catch((err: BusinessError) => {
      console.error(`setSpecificSystemBarEnabled failed, code: ${err.code}, message: ${err.message}`);
    });
  }
}
```
