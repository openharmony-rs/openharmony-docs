# @ohos.app.ability.CompletionHandlerForAbilityStartCallback (Application Launch Result Callback Handler)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

**CompletionHandlerForAbilityStartCallback** is an optional parameter of [AbilityStartCallback](js-apis-inner-application-abilityStartCallback.md). It provides callback results for launching ability components of specific types through the vertical panel.


> **NOTE**
>
> - The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { CompletionHandlerForAbilityStartCallback } from '@kit.AbilityKit';
```

## CompletionHandlerForAbilityStartCallback

**CompletionHandlerForAbilityStartCallback** provides two callback functions, **onRequestSuccess** and **onRequestFailure**, which are invoked when launching the specified ability succeeds or fails, respectively.

### Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                 | Type    | Read-Only  | Optional  | Description                                                              |
|---------------------| ------ | ---- | ---- |------------------------------------------------------------------|
| onRequestSuccess | [OnRequestSuccessFn](#onrequestsuccessfn) | No   | Yes   | Callback invoked when the specified ability is successfully launched.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| onRequestFailure     | [OnRequestFailureFn](#onrequestfailurefn) | No   | Yes   | Callback invoked when launching the specified ability fails.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|

## OnRequestSuccessFn 

type OnRequestSuccessFn = (name: string) => void

Defines the callback for successful ability launches.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Name of the launched ability or system operation.<br>The ability component name is in the format of '[bundleName]#[moduleName]#[abilityName]'.|

**Example**

See [OnRequestFailureFn](#onrequestfailurefn).

## OnRequestFailureFn

type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void

Defines the callback for failed ability launches.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Name of the launched ability or system operation.<br>The ability component name is in the format of '[bundleName]#[moduleName]#[abilityName]'. If the user cancels the launch automatically, this parameter is empty.|
| failureCode | [AbilityStartFailureCode](#abilitystartfailurecode) | Yes| Error code of the failure cause.|
| failureMessage | string | Yes| Description of the failure cause.|

**Example**

```ts
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
      console.info(`testTag code:` + code + `name:` + name + `message:` + message);
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
            console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
          });
        })
    }
  }
}

```

## AbilityStartFailureCode 

Enumerates the specific error codes for ability launch failures.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                                    | Value  | Description                                      |
| ---------------------------------------- | ---- | ---------------------------------------- |
| FAILURE_CODE_SYSTEM_MALFUNCTION     | 0    | The ability cannot be launched due to a system error (for example, a crash in starting the picker).|
| FAILURE_CODE_USER_CANCEL            | 1    | The user canceled the operation.|
