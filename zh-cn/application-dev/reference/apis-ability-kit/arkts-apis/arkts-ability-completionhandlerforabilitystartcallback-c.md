# CompletionHandlerForAbilityStartCallback

CompletionHandlerForAbilityStartCallback提供了onRequestSuccess和onRequestFailure两个回调函数属性，分别在拉起指定类型的Ability组件成功和失败时回调。

**起始版本：** 21

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onRequestFailure

```TypeScript
onRequestFailure?: OnRequestFailureFn
```

拉起指定类型的Ability组件失败时的回调函数。

从API version 21开始，该接口支持在原子化服务中使用。

**类型：** OnRequestFailureFn

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onRequestSuccess

```TypeScript
onRequestSuccess?: OnRequestSuccessFn
```

拉起指定类型的Ability组件成功时的回调函数。

从API version 21开始，该接口支持在原子化服务中使用。

**类型：** OnRequestSuccessFn

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

