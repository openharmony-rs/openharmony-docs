# PreferStrategy

```TypeScript
enum PreferStrategy
```

偏好策略。

以全局日志级别为INFO下，打印5条不同级别的hilog日志，在打印过程中调用两次setLogLevel接口为例：

由于全局日志起始为INFO，第一条日志可以正常打印。

在设置进程最低日志级别为WANR, 并选择策略PREFER_OPEN_LOG后，实际生效的最低日志级别是全局日志级别INFO，所以第二条和第三条日志均可正常打印。

在设置进程最低日志级别为DEBUG, 并选择策略PREFER_CLOSE_LOG后(等同于hilog.setMinLogLevel(hilog.LogLevel.DEBUG)), 但是此时全局日志级别为INFO，所以第四条日志不满足全

局日志级别，打印失败，第五条日志可以打印。

**起始版本：** 21

<!--Device-hilog-enum PreferStrategy--><!--Device-hilog-enum PreferStrategy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## PREFER_CLOSE_LOG

```TypeScript
PREFER_CLOSE_LOG = 1
```

实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较大值，适用于需要严格限制日志输出的场景

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1--><!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## PREFER_OPEN_LOG

```TypeScript
PREFER_OPEN_LOG = 2
```

实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较小值，适用于需要尽可能多的打开日志输出的场景

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PreferStrategy-PREFER_OPEN_LOG = 2--><!--Device-PreferStrategy-PREFER_OPEN_LOG = 2-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## UNSET_LOGLEVEL

```TypeScript
UNSET_LOGLEVEL = 0
```

清除设置, 实际生效的最低日志级别是系统控制的最低级别。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务中使用。

<!--Device-PreferStrategy-UNSET_LOGLEVEL = 0--><!--Device-PreferStrategy-UNSET_LOGLEVEL = 0-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog
