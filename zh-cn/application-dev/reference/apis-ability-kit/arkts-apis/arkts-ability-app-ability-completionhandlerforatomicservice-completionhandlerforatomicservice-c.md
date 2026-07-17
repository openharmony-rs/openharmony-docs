# CompletionHandlerForAtomicService

CompletionHandlerForAtomicService提供了[onAtomicServiceRequestSuccess](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md#onatomicservicerequestsuccess-1)和[onAtomicServiceRequestFailure](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md#onatomicservicerequestfailure-1)两个回调函数，分别在打开原子化服务成功和失败时回调。

**起始版本：** 20

<!--Device-unnamed-declare class CompletionHandlerForAtomicService--><!--Device-unnamed-declare class CompletionHandlerForAtomicService-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { FailureCode } from '@kit.AbilityKit';
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

**示例：**

参见[CompletionHandlerForAtomicService示例](#completionhandlerforatomicservice示例)。

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

**示例：**

参见[CompletionHandlerForAtomicService示例](#completionhandlerforatomicservice示例)。

