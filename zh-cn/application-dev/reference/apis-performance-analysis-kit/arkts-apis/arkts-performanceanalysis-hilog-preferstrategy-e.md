# PreferStrategy

偏好策略。

**起始版本：** 21

**系统能力：** SystemCapability.HiviewDFX.HiLog

## UNSET_LOGLEVEL

```TypeScript
UNSET_LOGLEVEL = 0
```

清除设置, 实际生效的最低日志级别是系统控制的最低级别。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiLog

## PREFER_CLOSE_LOG

```TypeScript
PREFER_CLOSE_LOG = 1
```

实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较大值。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiLog

## PREFER_OPEN_LOG

```TypeScript
PREFER_OPEN_LOG = 2
```

实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较小值。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiLog

**示例**

以全局日志级别为INFO下，打印5条不同级别的hilog日志，在打印过程中调用两次setLogLevel接口为例：

```TypeScript
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 1);
hilog.setLogLevel(hilog.LogLevel.WARN, hilog.PreferStrategy.PREFER_OPEN_LOG);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 2);
hilog.error(0x0001, 'testTag', 'this is an error level log, id: %{public}d', 3);
hilog.setLogLevel(hilog.LogLevel.DEBUG, hilog.PreferStrategy.PREFER_CLOSE_LOG);
hilog.debug(0x0001, "testTag", 'this is a debug level log, id: %{public}d', 4);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 5);
```

最终打印结果如下所示：

```TypeScript
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 1
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 2
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  E     this is an error level log, id: 3
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 5
```
