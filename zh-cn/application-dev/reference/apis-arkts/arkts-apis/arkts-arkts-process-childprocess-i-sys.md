# ChildProcess（系统接口）

childprocess 对象可用于创建新的进程。

**起始版本：** 7

<!--Device-process-export interface ChildProcess--><!--Device-process-export interface ChildProcess-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## close

```TypeScript
close(): void
```

关闭目标进程。

**起始版本：** 7

<!--Device-ChildProcess-close(): void--><!--Device-ChildProcess-close(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## getErrorOutput

```TypeScript
getErrorOutput(): Promise<Uint8Array>
```

返回子进程的标准错误输出，以 Uint8Array 形式返回直到 EOF。

**起始版本：** 7

<!--Device-ChildProcess-getErrorOutput(): Promise<Uint8Array>--><!--Device-ChildProcess-getErrorOutput(): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 返回子进程的标准错误输出。 |

## getOutput

```TypeScript
getOutput(): Promise<Uint8Array>
```

返回子进程的标准输出，以 Uint8Array 形式返回直到 EOF。

**起始版本：** 7

<!--Device-ChildProcess-getOutput(): Promise<Uint8Array>--><!--Device-ChildProcess-getOutput(): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 返回子进程的标准输出。 |

## kill

```TypeScript
kill(signal: number | string): void
```

向进程发送信号。

**起始版本：** 7

<!--Device-ChildProcess-kill(signal: number | string): void--><!--Device-ChildProcess-kill(signal: number | string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| signal | number \| string | 是 | number 或 string，表示发送的信号。 |

## wait

```TypeScript
wait(): Promise<number>
```

返回 number 表示目标进程的退出码。

**起始版本：** 7

<!--Device-ChildProcess-wait(): Promise<number>--><!--Device-ChildProcess-wait(): Promise<number>-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 返回目标进程的退出码。 |

## exitCode

```TypeScript
readonly exitCode: number
```

返回 exitCode 表示当前子进程的退出码。

**类型：** number

**起始版本：** 7

<!--Device-ChildProcess-readonly exitCode: number--><!--Device-ChildProcess-readonly exitCode: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## killed

```TypeScript
readonly killed: boolean
```

返回 boolean 表示当前进程信号是否发送成功。

**类型：** boolean

**起始版本：** 7

<!--Device-ChildProcess-readonly killed: boolean--><!--Device-ChildProcess-readonly killed: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## pid

```TypeScript
readonly pid: number
```

返回 pid 表示当前进程的 pid。

**类型：** number

**起始版本：** 7

<!--Device-ChildProcess-readonly pid: number--><!--Device-ChildProcess-readonly pid: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## ppid

```TypeScript
readonly ppid: number
```

返回 ppid 表示当前子进程的 pid。

**类型：** number

**起始版本：** 7

<!--Device-ChildProcess-readonly ppid: number--><!--Device-ChildProcess-readonly ppid: number-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

