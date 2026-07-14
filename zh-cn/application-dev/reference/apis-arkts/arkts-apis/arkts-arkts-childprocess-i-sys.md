# ChildProcess（系统接口）

childprocess 对象可用于创建新的进程。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## close

```TypeScript
close(): void
```

关闭目标进程。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## getErrorOutput

```TypeScript
getErrorOutput(): Promise<Uint8Array>
```

返回子进程的标准错误输出，以 Uint8Array 形式返回直到 EOF。

**起始版本：** 7

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

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## killed

```TypeScript
readonly killed: boolean
```

返回 boolean 表示当前进程信号是否发送成功。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## pid

```TypeScript
readonly pid: number
```

返回 pid 表示当前进程的 pid。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## ppid

```TypeScript
readonly ppid: number
```

返回 ppid 表示当前子进程的 pid。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

