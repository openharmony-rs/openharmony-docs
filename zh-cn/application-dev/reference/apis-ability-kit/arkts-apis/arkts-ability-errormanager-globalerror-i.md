# GlobalError

有关异常事件名字、消息、错误堆栈信息、异常线程名称和类型的对象。

**继承/实现关系：** GlobalError extends [Error](Error)

**起始版本：** 18

<!--Device-errorManager-export interface GlobalError extends Error--><!--Device-errorManager-export interface GlobalError extends Error-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

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

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalError-instanceName: string--><!--Device-GlobalError-instanceName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## instanceType

```TypeScript
instanceType: InstanceType
```

表示虚拟机的实例类型。

**类型：** InstanceType

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalError-instanceType: InstanceType--><!--Device-GlobalError-instanceType: InstanceType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

