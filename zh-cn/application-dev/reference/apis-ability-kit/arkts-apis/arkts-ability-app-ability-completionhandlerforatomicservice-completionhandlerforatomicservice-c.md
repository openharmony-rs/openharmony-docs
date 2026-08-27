# CompletionHandlerForAtomicService

CompletionHandlerForAtomicService提供了 [onAtomicServiceRequestSuccess](#onatomicservicerequestsuccess) 和 [onAtomicServiceRequestFailure](#onatomicservicerequestfailure) 两个回调函数，分别在打开原子化服务成功和失败时回调。

**起始版本：** 20

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

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |
| failureCode | [FailureCode](arkts-ability-app-ability-completionhandlerforatomicservice-failurecode-e.md) | 是 | 失败原因的错误码。 |
| failureMessage | string | 是 | 失败原因的描述。 |

**示例**

参见CompletionHandlerForAtomicService示例。

## onAtomicServiceRequestSuccess

```TypeScript
onAtomicServiceRequestSuccess(appId: string): void
```

打开原子化服务成功时的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |

**示例**

参见CompletionHandlerForAtomicService示例。
