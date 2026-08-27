# HiTraceOutputLevel

枚举，跟踪输出级别。低于系统跟踪输出级别阈值的打点将不会生效。log版本阈值为INFO；nolog版本阈值为COMMERCIAL。

**起始版本：** 19

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DEBUG

```TypeScript
DEBUG = 0
```

仅用于调试的输出级别，优先级最低。低于系统跟踪输出级别阈值时打点不会生效。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## INFO

```TypeScript
INFO = 1
```

用于log版本的输出级别，log版本阈值为INFO。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## CRITICAL

```TypeScript
CRITICAL = 2
```

用于log版本的输出级别，优先级高于INFO，用于需要重点关注的trace事件。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## COMMERCIAL

```TypeScript
COMMERCIAL = 3
```

用于nolog版本的输出级别，优先级最高。nolog版本阈值为COMMERCIAL。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## MAX

```TypeScript
MAX = COMMERCIAL
```

输出级别范围限制，MAX = COMMERCIAL。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace
