# runCmd（系统接口）

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## runCmd

```TypeScript
function runCmd(
    command: string,
    options?: ConditionType
  ): ChildProcess
```

返回一个子进程对象，并 spawn 一个新的 ChildProcess 来运行命令。

**起始版本：** 7

<!--Device-process-function runCmd(
    command: string,
    options?: ConditionType
  ): ChildProcess--><!--Device-process-function runCmd(
    command: string,
    options?: ConditionType
  ): ChildProcess-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 子进程执行的 shell 命令字符串。 |
| options | [ConditionType](arkts-arkts-process-conditiontype-i-sys.md) | 否 | 是一个对象，包含三个参数。timeout 是子进程的运行时间，killSignal 是子进程达到 timeout 时发送的信号，maxBuffer 是标准输入和输出的最大缓冲区大小。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ChildProcess](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-childprocess-childprocess-c.md) | 返回一个子进程对象。 |

