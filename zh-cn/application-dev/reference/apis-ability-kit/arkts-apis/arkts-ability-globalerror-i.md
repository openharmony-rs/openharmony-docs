# GlobalError

有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。

**继承/实现关系：** GlobalError extends [Error](Error)

**起始版本：** 18

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## instanceName

```TypeScript
instanceName: string
```

表示虚拟机实例名称。

**说明**：

TaskPool线程中异常的instanceName标识规则：

- globalErrorOccurred：标识为“TaskPool Thread + 方法名”；
- globalUnhandledRejectionDetected：标识为“TaskPool Thread + 任务名”；
- 若仅标识为“TaskPool Thread”，则表明异常源于异步回调内部。

**类型：** string

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## instanceType

```TypeScript
instanceType: InstanceType
```

表示虚拟机的实例类型。

**类型：** InstanceType

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

