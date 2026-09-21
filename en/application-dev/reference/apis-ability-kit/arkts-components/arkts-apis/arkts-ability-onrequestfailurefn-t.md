# OnRequestFailureFn

```TypeScript
export type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void
```

Defines the callback for failed ability launches.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the launched ability or system operation. The ability component name is in the format of '[bundleName]#[moduleName]#[abilityName]'. If the user cancels the launch automatically, this parameter is empty. |
| failureCode | [AbilityStartFailureCode](arkts-ability-app-ability-completionhandlerforabilitystartcallback-abilitystartfailurecode-e.md) | Yes | Error code of the failure cause. |
| failureMessage | string | Yes | Description of the failure cause. |

**Examples**

```TypeScript
import { AbilityStartFailureCode, common, CompletionHandlerForAbilityStartCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

  completionHandler: CompletionHandlerForAbilityStartCallback = {
    onRequestSuccess: (name: string) => {
      console.info(`testTag onRequestSuccess name` + name);
    },
    onRequestFailure: (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => {
      console.info(`testTag onRequestFailure name: ` + name + `, failureCode:` + failureCode + `, failureMessage:` +
        failureMessage);
    }
  };
  abilityStartCallback: common.AbilityStartCallback = {
    onError: (code: number, name: string, message: string) => {
      console.error(`testTag code:` + code + `name:` + name + `message:` + message);
    },
    onResult: (abilityResult: common.AbilityResult) => {
      console.info(`testTag resultCode:` + abilityResult.resultCode + `bundleName:` + abilityResult.want?.bundleName);
    },
    completionHandler: this.completionHandler,
  };

  build() {
    Column({ space: 10 }) {
      Button('test')
        .type(ButtonType.Capsule)
        .offset({ x: 0, y: 60 })
        .width('80%')
        .type(ButtonType.Capsule)
        .margin({ top: 10 })
        .onClick(() => {
          let wantParam: Record<string, Object> = {
            'time': '2023-10-23 20:45'
          };
          this.context.startAbilityByType("share", wantParam, this.abilityStartCallback).then(() => {
            console.info(`startAbilityByType success`);
          }).catch((err: BusinessError) => {
            console.error(`Failed startAbilityByType. Code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`);
          });
        })
    }
  }
}
```
