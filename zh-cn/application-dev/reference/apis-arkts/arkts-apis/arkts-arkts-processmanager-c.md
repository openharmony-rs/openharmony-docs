# ProcessManager

提供进程管理相关接口，包括进程 UID 判断、用户信息查询、线程优先级获取、环境变量获取、进程退出和信号发送等功能。

通过 `new process.ProcessManager()` 构造 ProcessManager 对象。

**起始版本：** 9

**系统能力：** SystemCapability.Utils.Lang

## exit

```TypeScript
exit(code: number): void
```

终止程序。

请谨慎使用此接口，此接口调用后应用会退出，如果入参非 0 会产生数据丢失或者异常情况。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 进程的退出码。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
pro.exit(0);

```

## getEnvironmentVar

```TypeScript
getEnvironmentVar(name: string): string
```

获取环境变量对应的值。

> **说明**
>
> 获取环境变量的值。如果环境变量不存在，返回 **undefined**。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 环境变量名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定环境变量名对应的值。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
let pres = pro.getEnvironmentVar("PATH");

```

## getSystemConfig

```TypeScript
getSystemConfig(name: number): number
```

获取系统配置信息。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | number | 是 | 指定系统配置参数名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回系统配置信息。如果配置不存在，返回 -1。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
let _SC_ARG_MAX = 0;
let pres = pro.getSystemConfig(_SC_ARG_MAX);

```

## getThreadPriority

```TypeScript
getThreadPriority(v: number): number
```

根据指定的 tid 获取线程优先级。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| v | number | 是 | 指定的线程 tid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回线程的优先级。优先级顺序取决于当前操作系统。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
let tid = process.tid;
let pres = pro.getThreadPriority(tid);

```

## getUidForName

```TypeScript
getUidForName(v: string): number
```

根据指定的用户名，从系统的用户数据库中获取该用户 uid。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| v | string | 是 | 用户名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取用户 uid，如果用户不存在则返回 -1。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
let pres = pro.getUidForName("tool");

```

## isAppUid

```TypeScript
isAppUid(v: number): boolean
```

判断 uid 是否属于当前应用程序。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| v | number | 是 | 应用程序的 uid。可通过 process.uid 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回判断结果。如果是应用程序的 uid 则返回 true；否则返回 false。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
// uid通过process.uid获取
let pres = process.uid;
let result = pro.isAppUid(pres);
console.info("result: " + result); // result: true

```

## kill

```TypeScript
kill(signal: number, pid: number): boolean
```

发送 signal 到指定的进程，结束指定进程（仅支持结束本进程）。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| signal | number | 是 | 发送特定的信号给目标进程。取值范围：1 &lt;= signal &lt;= 64。 |
| pid | number | 是 | 进程的 id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 信号是否发送成功。如果信号发送成功则返回 true；否则返回 false。 |

**示例：**

```TypeScript
let pro = new process.ProcessManager();
let pres = process.pid;
let result = pro.kill(28, pres);

```

