# GlobalError

有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。

**继承/实现关系：** GlobalError extends [Error](../../apis-arkweb/arkts-components/arkts-arkweb-messagelevel-e.md#Error)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-errorManager-export interface GlobalError--><!--Device-errorManager-export interface GlobalError-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## instanceName

```TypeScript
instanceName: string
```

表示虚拟机实例名称。 **说明：** TaskPool线程中异常的instanceName标识规则： - globalErrorOccurred：标识为“TaskPool Thread + 方法名”； - globalUnhandledRejectionDetected：标识为“TaskPool Thread + 任务名”； - 若仅标识为“TaskPool Thread”，则表明异常源于异步回调内部。

**类型：** string

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalError-instanceName: string--><!--Device-GlobalError-instanceName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## instanceType

```TypeScript
instanceType: InstanceType
```

表示虚拟机的实例类型。

**类型：** [InstanceType](arkts-ability-errormanager-instancetype-e.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalError-instanceType: InstanceType--><!--Device-GlobalError-instanceType: InstanceType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

