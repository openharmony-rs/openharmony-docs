# LogLevel

日志级别。

**起始版本：** 7

<!--Device-hilog-enum LogLevel--><!--Device-hilog-enum LogLevel-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## DEBUG

```TypeScript
DEBUG = 3
```

详细的流程记录，通过该级别的日志可以更详细地分析业务流程和定位分析问题。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LogLevel-DEBUG = 3--><!--Device-LogLevel-DEBUG = 3-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## INFO

```TypeScript
INFO = 4
```

用于记录业务关键流程节点，可以还原业务的主要运行过程；

用于记录可预料的非正常情况信息，如无网络信号、登录失败等。

这些日志都应该由该业务内处于支配地位的模块来记录，避免在多个被调用的模块或低级函数中重复记录。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LogLevel-INFO = 4--><!--Device-LogLevel-INFO = 4-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## WARN

```TypeScript
WARN = 5
```

用于记录较为严重的非预期情况，但是对用户影响不大，应用可以自动恢复或通过简单的操作就可以恢复的问题。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LogLevel-WARN = 5--><!--Device-LogLevel-WARN = 5-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## ERROR

```TypeScript
ERROR = 6
```

应用发生了错误，该错误会影响功能的正常运行或用户的正常使用，可以恢复但恢复代价较高，如重置数据等。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LogLevel-ERROR = 6--><!--Device-LogLevel-ERROR = 6-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## FATAL

```TypeScript
FATAL = 7
```

重大致命异常，表明应用即将崩溃，故障无法恢复。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LogLevel-FATAL = 7--><!--Device-LogLevel-FATAL = 7-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

