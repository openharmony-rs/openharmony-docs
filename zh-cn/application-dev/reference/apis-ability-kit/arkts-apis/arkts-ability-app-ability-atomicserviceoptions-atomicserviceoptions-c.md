# AtomicServiceOptions

**AtomicServiceOptions** is used as an input parameter of [openAtomicService()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ to carry arguments. It inherits from [StartOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_.

**继承/实现关系：** AtomicServiceOptions extends [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md)

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export default class AtomicServiceOptions extends StartOptions--><!--Device-unnamed-export default class AtomicServiceOptions extends StartOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## completionHandlerForAtomicService

```TypeScript
completionHandlerForAtomicService?: CompletionHandlerForAtomicService
```

打开原子化服务结果的操作类，用于接收打开原子化服务的结果。

**类型：** CompletionHandlerForAtomicService

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService--><!--Device-AtomicServiceOptions-completionHandlerForAtomicService?: CompletionHandlerForAtomicService-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## flags

```TypeScript
flags?: int
```

系统处理该次启动的方式。例如通过wantConstant.Flags.FLAG\_INSTALL\_ON\_DEMAND表示使用免安装能力。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceOptions-flags?: int--><!--Device-AtomicServiceOptions-flags?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示额外参数描述。具体描述参考[Want]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中parameters字段描述。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceOptions-parameters?: Record<string, Object>--><!--Device-AtomicServiceOptions-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

