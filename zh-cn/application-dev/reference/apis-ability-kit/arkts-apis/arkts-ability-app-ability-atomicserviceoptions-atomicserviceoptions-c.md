# AtomicServiceOptions

**AtomicServiceOptions** is used as an input parameter of [openAtomicService()](arkts-ability-uiabilitycontext-c.md#openAtomicService) to carry arguments. It inherits from [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md#StartOptions).

**继承/实现关系：** AtomicServiceOptions extends [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md#StartOptions)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export default class AtomicServiceOptions--><!--Device-unnamed-export default class AtomicServiceOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## completionHandlerForAtomicService

```TypeScript
completionHandlerForAtomicService?: CompletionHandlerForAtomicService
```

打开原子化服务结果的操作类，用于接收打开原子化服务的结果。

**类型：** [CompletionHandlerForAtomicService](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService--><!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: int
```

系统处理该次启动的方式。例如通过wantConstant.Flags.FLAG_INSTALL_ON_DEMAND表示使用免安装能力。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceOptions-flags?: int--><!--Device-AtomicServiceOptions-flags?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, RecordData>
```

表示额外参数描述。具体描述参考[Want](arkts-ability-app-ability-want-want-c.md#Want)中parameters字段描述。

**类型：** Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceOptions-parameters?: Record<string, RecordData>--><!--Device-AtomicServiceOptions-parameters?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

