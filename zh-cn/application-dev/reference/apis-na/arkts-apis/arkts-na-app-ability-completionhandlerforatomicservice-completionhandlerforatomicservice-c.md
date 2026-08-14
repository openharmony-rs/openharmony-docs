# CompletionHandlerForAtomicService

CompletionHandlerForAtomicService提供了 [onAtomicServiceRequestSuccess](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md#onAtomicServiceRequestSuccess) 和 [onAtomicServiceRequestFailure](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md#onAtomicServiceRequestFailure) 两个回调函数，分别在打开原子化服务成功和失败时回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class CompletionHandlerForAtomicService--><!--Device-unnamed-declare class CompletionHandlerForAtomicService-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAtomicServiceRequestFailure

```TypeScript
onAtomicServiceRequestFailure: OnAtomicServiceRequestFailureFn
```

打开原子化服务失败时的回调函数。

**类型：** [OnAtomicServiceRequestFailureFn](arkts-na-onatomicservicerequestfailurefn-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestFailure: OnAtomicServiceRequestFailureFn--><!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestFailure: OnAtomicServiceRequestFailureFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAtomicServiceRequestSuccess

```TypeScript
onAtomicServiceRequestSuccess: OnAtomicServiceRequestSuccessFn
```

打开原子化服务成功时的回调函数。

**类型：** [OnAtomicServiceRequestSuccessFn](arkts-na-onatomicservicerequestsuccessfn-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestSuccess: OnAtomicServiceRequestSuccessFn--><!--Device-CompletionHandlerForAtomicService-onAtomicServiceRequestSuccess: OnAtomicServiceRequestSuccessFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

