# AtomicServiceOptions

**AtomicServiceOptions** is used as an input parameter of
[openAtomicService()](arkts-ability-uiabilitycontext-c.md#openatomicservice-1) to carry arguments. It
inherits from [StartOptions](arkts-ability-startoptions-c.md).

**继承/实现关系：** AtomicServiceOptions extends [StartOptions](arkts-ability-startoptions-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## completionHandlerForAtomicService

```TypeScript
completionHandlerForAtomicService?: CompletionHandlerForAtomicService
```

打开原子化服务结果的操作类，用于接收打开原子化服务的结果。

**类型：** CompletionHandlerForAtomicService

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: number
```

系统处理该次启动的方式。例如通过wantConstant.Flags.FLAG_INSTALL_ON_DEMAND表示使用免安装能力。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示额外参数描述。具体描述参考[Want](arkts-ability-want-c.md)中parameters字段描述。

**类型：** Record<string, Object>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

