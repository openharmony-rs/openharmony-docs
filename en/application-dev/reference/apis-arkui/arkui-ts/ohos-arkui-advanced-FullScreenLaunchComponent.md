# FullScreenLaunchComponent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @autojuan-->
<!--Designer: @autojuan-->
<!--Tester: @wonlee-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=215122c8ace12b6255c403e4a84ede7537bff66c translatedAt=2026-08-28T01:31:54.392Z pushedAt=2026-08-28T06:10:04.834Z -->

A component for launching atomic services in full screen. When the provider grants the invoker the authorization to run the atomic service in embedded mode, the invoker runs the atomic service in full-screen embedded mode; otherwise, the invoker launches the atomic service in jump-out mode.

> **NOTE**
>
> This component is supported since API version 12. New APIs added in later versions are marked with a superscript to indicate their earliest API version.
>
> To implement an atomic service that can run in embedded mode in this component, the atomic service must inherit from [EmbeddableUIAbility](../../apis-ability-kit/js-apis-app-ability-embeddableUIAbility.md). Otherwise, the system cannot guarantee that the atomic service functions properly.

## Modules to Import

```ts
import { FullScreenLaunchComponent } from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## FullScreenLaunchComponent

FullScreenLaunchComponent({ content: Callback\<void>, appId: string, options?: AtomicServiceOptions, onError?: ErrorCallback, onTerminated?: Callback\<TerminationInfo>, onReceive?: Callback\<Record<string, Object>> })

**Decorator:** [@Component](../../../ui/state-management/arkts-create-custom-components.md#component)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Decorator Type| Description|
| -------- | -------- | -------- | -------- | -------- |
| content | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<void> | Yes | [@BuilderParam](../../../ui/state-management/arkts-builderparam.md) | Custom placeholder icon displayed before the atomic service is launched, which can be composed of components to achieve an effect similar to a large desktop app icon. Tapping the placeholder component launches the atomic service. |
| appId | string | Yes | - | **appId** of the atomic service to be launched. The **appId** is the unique identifier of the atomic service. |
| options | [AtomicServiceOptions](../../apis-ability-kit/js-apis-app-ability-atomicServiceOptions.md) | No | - | Parameters for launching the atomic service. If this parameter is not set, the default parameters are used to launch the atomic service. |
| onError<sup>18+</sup> | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | No | - | Callback invoked when an exception occurs during the running of the launched atomic service in embedded running mode. The error information can be obtained and processed through the **code**, **name**, and **message** parameters in the callback.<br>**Atomic service API:** This API can be used in atomic services since API version 18. |
| onTerminated<sup>18+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](ts-container-embedded-component.md#terminationinfo)> | No | - | Callback invoked when the launched atomic service in embedded running mode exits normally by tapping the exit button of the atomic service, swiping sideways, or calling [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself).<br>**Atomic service API:** This API can be used in atomic services since API version 18. |
| onReceive<sup>20+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record<string, Object>> | No | - | Callback invoked when the launched atomic service in embedded running mode calls related APIs through [@ohos.window (Window)](../arkts-apis-window.md).<br>**Atomic service API:** This API can be used in atomic services since API version 20. |

> **NOTE**
>
> - If the atomic service exits by calling [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult), the information it carries is passed to the input parameter of the callback.
> - If the atomic service exits by calling [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself), in the input parameter of the callback, "code" takes the default value "0" and "want" is "undefined".
> - Since API version 26.0.0, the **onTerminated** callback is triggered when the atomic service exits through a side-swipe gesture.

## Example

This example demonstrates how to use the component and how to implement the provider-side atomic service. In actual running, use the **appId** of your own atomic service.

The **FullScreenLaunchComponent** component must be invoked by the invoker. After the provider completes local installation, the provider's atomic service can be launched in full-screen embedded mode in the invoker's app or atomic service.

> **NOTE**
>
> Because the embedded atomic service runs in an independent process, its crash exceptions are not directly exposed in the host's logs. During local debugging, you can view the actual error stack as follows:  
> 1. Open the HiLog panel in DevEco Studio.  
> 2. Switch the mode in the upper left corner to User logs of selected app.  
> 3. In the process list on the right, select the launched atomic service process (the bundle name of the launched atomic service, with the suffix "embeddable").

**User Implementation**

```ts
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

**Provider Implementation**

You need to modify the following files for the atomic service provider:

- Entry point file: **/src/main/ets/entryability/EntryAbility.ets**

```ts
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

- Extended ability entry page file: **/src/main/ets/pages/Index.ets**

```ts
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