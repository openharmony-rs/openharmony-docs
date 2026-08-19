# ConditionType（系统接口）

提供 ConditionType 类型，包括 timeout、killSignal、maxBuffer。

**起始版本：** 10

<!--Device-process-interface ConditionType--><!--Device-process-interface ConditionType-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## killSignal

```TypeScript
killSignal?: number | string
```

当子进程运行时间超过 timeout 时，向子进程发送的信号。

**类型：** number \| string

**起始版本：** 10

<!--Device-ConditionType-killSignal?: number | string--><!--Device-ConditionType-killSignal?: number | string-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## maxBuffer

```TypeScript
maxBuffer?: number
```

子进程标准输入和输出的最大缓冲区大小。

**类型：** number

**起始版本：** 10

<!--Device-ConditionType-maxBuffer?: number--><!--Device-ConditionType-maxBuffer?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## timeout

```TypeScript
timeout?: number
```

子进程的最大运行时间（单位：毫秒）。

**类型：** number

**起始版本：** 10

<!--Device-ConditionType-timeout?: number--><!--Device-ConditionType-timeout?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

