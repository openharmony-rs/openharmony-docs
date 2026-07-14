# setMinLogLevel

## setMinLogLevel

```TypeScript
function setMinLogLevel(level: LogLevel): void
```

设置应用日志打印的最低日志级别，用于拦截低级别日志打印。

> **注意：**
>
> 如果设置的日志级别低于[全局日志级别](../../../../dfx/hilog.md#查看和设置日志级别)，设置不生效。
>
> debug版本应用下，此函数不生效。

**起始版本：** 15

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiLog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | LogLevel | 是 | 日志级别。 |

**示例：**

以全局日志级别为INFO下，打印5条不同级别的hilog日志，在打印过程中调用两次setMinLogLevel接口为例：

```TypeScript
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 1);
hilog.setMinLogLevel(hilog.LogLevel.WARN);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 2);
hilog.error(0x0001, "testTag", 'this is an error level log, id: %{public}d', 3);
hilog.setMinLogLevel(hilog.LogLevel.DEBUG);
hilog.debug(0x0001, "testTag", 'this is a debug level log, id: %{public}d', 4);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 5);

```

最终打印结果如下所示：

```TypeScript
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 1
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  E     this is an error level log, id: 3
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 5

```

