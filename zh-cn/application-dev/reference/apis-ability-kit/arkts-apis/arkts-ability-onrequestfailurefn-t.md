# OnRequestFailureFn

```TypeScript
export type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void
```

拉起指定类型的Ability组件失败时的回调函数类型。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 被拉起Ability组件或系统操作的名称。 Ability组件名称采用'[bundleName]#[moduleName]#[abilityName]'格式拼接。如果用户自动取消拉起，name为空。 |
| failureCode | [AbilityStartFailureCode](arkts-ability-app-ability-completionhandlerforabilitystartcallback-abilitystartfailurecode-e.md) | 是 | 失败原因的错误码。 |
| failureMessage | string | 是 | 失败原因的描述。 |

**示例**

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
