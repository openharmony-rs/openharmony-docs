# CompletionHandlerForAtomicService

CompletionHandlerForAtomicService提供了 [onAtomicServiceRequestSuccess](#onatomicservicerequestsuccess) 和 [onAtomicServiceRequestFailure](#onatomicservicerequestfailure) 两个回调函数，分别在打开原子化服务成功和失败时回调。

**起始版本：** 20

<!--Device-unnamed-declare class CompletionHandlerForAtomicService--><!--Device-unnamed-declare class CompletionHandlerForAtomicService-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { CompletionHandlerForAtomicService, FailureCode } from '@kit.AbilityKit';
```

## onAtomicServiceRequestFailure

```TypeScript
onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string): void
```

打开原子化服务失败时的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string): void--><!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |
| failureCode | [FailureCode](arkts-ability-app-ability-completionhandlerforatomicservice-failurecode-e.md) | 是 | 失败原因的错误码。 |
| failureMessage | string | 是 | 失败原因的描述。 |

**示例**

```TypeScript
import { AbilityConstant, AtomicServiceOptions, common, UIAbility, Want, CompletionHandlerForAtomicService, FailureCode } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let completionHandler: CompletionHandlerForAtomicService = {
      // 定义原子化服务请求成功的回调函数
      onAtomicServiceRequestSuccess(appId: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}`);
      },
      // 定义原子化服务请求失败的回调函数
      onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string) {
        hilog.info(0x0000, 'testTag', `appId:${appId}, failureCode:${failureCode}, failureMessage:${failureMessage}`);
      }
    };
    // 创建原子化服务对象
    let options: AtomicServiceOptions = {
      completionHandlerForAtomicService: completionHandler
    };
    let appId: string = '5765880207853275489'; // 根据实际appId修改此值
    this.context.openAtomicService(appId, options).then((result: common.AbilityResult) => {
      hilog.info(0x0000, 'testTag', `openAtomicService succeed:${JSON.stringify(result)}`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `openAtomicService failed:${JSON.stringify(err)}`);
    });
  }
}
```

## onAtomicServiceRequestSuccess

```TypeScript
onAtomicServiceRequestSuccess(appId: string): void
```

打开原子化服务成功时的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestSuccess(appId: string): void--><!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestSuccess(appId: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |

**示例**

参见[onAtomicServiceRequestFailure](#onatomicservicerequestfailure)接口的示例。

