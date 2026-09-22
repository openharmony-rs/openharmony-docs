# @ohos.arkui.advanced.FullScreenLaunchComponent(Defines the fullScreen launch component)

## Child Components

Not supported

## Attributes

The [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { FullScreenLaunchComponent } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [FullScreenLaunchComponent](arkts-arkui-arkui-advanced-fullscreenlaunchcomponent-fullscreenlaunchcomponent-s.md) | **FullScreenLaunchComponent** is a component designed for launching atomic services in full screen. If the invoked app (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in full-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner. |

## Examples

This example demonstrates how to use the component and how to implement the provider-side atomic service. In actual running, use the appId of your own atomic service.

The FullScreenLaunchComponent component must be invoked by the invoker. After the provider completes local installation, the provider's atomic service can be launched in full-screen embedded mode in the invoker's app or atomic service.

> NOTE
> 
> Because the embedded atomic service runs in an independent process, its crash exceptions are not directly exposed in the host's logs. During local debugging, you can view the actual error stack as follows:
> 
> Open the HiLog panel in DevEco Studio.
> 
> Switch the mode in the upper left corner to User logs of selected app.
> 
> In the process list on the right, select the launched atomic service process (the bundle name of the launched atomic service, with the suffix "embeddable").

User Implementation

```TypeScript
// The content of the consumer entry page Index.ets is as follows:
import { FullScreenLaunchComponent } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State appId: string = '6917573653426122083'; // Application ID of the atomic service.

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

Provider Implementation

You need to modify the following files for the atomic service provider:

Entry point file: /src/main/ets/entryability/EntryAbility.ets

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

Extended ability entry page file: /src/main/ets/pages/Index.ets

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
