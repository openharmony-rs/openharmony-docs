# PreferStrategy

偏好策略。

**起始版本：** 21

<!--Device-hilog-enum PreferStrategy--><!--Device-hilog-enum PreferStrategy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## UNSET_LOGLEVEL

```TypeScript
UNSET_LOGLEVEL = 0
```

清除设置, 实际生效的最低日志级别是系统控制的最低级别。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PreferStrategy-UNSET_LOGLEVEL = 0--><!--Device-PreferStrategy-UNSET_LOGLEVEL = 0-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## PREFER_CLOSE_LOG

```TypeScript
PREFER_CLOSE_LOG = 1
```

实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较大值。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1--><!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## PREFER_OPEN_LOG

```TypeScript
PREFER_OPEN_LOG = 2
```

实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较小值。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PreferStrategy-PREFER_OPEN_LOG = 2--><!--Device-PreferStrategy-PREFER_OPEN_LOG = 2-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

