# CompletionHandlerForAtomicService

CompletionHandlerForAtomicService提供了
[onAtomicServiceRequestSuccess](arkts-ability-completionhandlerforatomicservice-c.md#onatomicservicerequestsuccess-1)
和
[onAtomicServiceRequestFailure](arkts-ability-completionhandlerforatomicservice-c.md#onatomicservicerequestfailure-1)
两个回调函数，分别在打开原子化服务成功和失败时回调。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAtomicServiceRequestFailure

```TypeScript
onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string): void
```

打开原子化服务失败时的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |
| failureCode | FailureCode | 是 | 失败原因的错误码。 |
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

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |

**示例：**

参见[CompletionHandlerForAtomicService示例](#completionhandlerforatomicservice示例)。

