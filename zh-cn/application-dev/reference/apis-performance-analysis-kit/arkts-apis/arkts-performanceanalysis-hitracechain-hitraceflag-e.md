# HiTraceFlag

跟踪标志组合类型枚举。用于控制分布式跟踪的行为模式，例如在需要跟踪异步调用的业务流程中使用INCLUDE_ASYNC标志，在不需要详细分支信息的简单业务 流程中使用DONOT_CREATE_SPAN标志，在需要调试埋点信息的场景中使用TP_INFO标志。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认标志。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## INCLUDE_ASYNC

```TypeScript
INCLUDE_ASYNC = 1
```

异步调用标志。设置该标志，同时跟踪同步和异步调用；默认只跟踪同步调用。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DONOT_CREATE_SPAN

```TypeScript
DONOT_CREATE_SPAN = 1 << 1
```

无分支标志。设置该标志，不创建分支信息；默认创建分支信息。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## TP_INFO

```TypeScript
TP_INFO = 1 << 2
```

埋点标志。设置该标志后，调用[tracepoint()](arkts-performanceanalysis-hitracechain-tracepoint-f.md)接口时会打印埋点信息hilog；默认不打印埋点信息hilog日志。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## NO_BE_INFO

```TypeScript
NO_BE_INFO = 1 << 3
```

无开始结束信息标志。调试场景下设置该标志，调用开始跟踪接口[begin()](arkts-performanceanalysis-hitracechain-begin-f.md)和结束跟踪接口[end()](arkts-performanceanalysis-hitracechain-end-f.md)时， 分别会打印开始、结束跟踪信息hilo日志；默认不打印开始、结束跟踪信息hilog日志。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DISABLE_LOG

```TypeScript
DISABLE_LOG = 1 << 4
```

日志关联标志。设置该标志，不会在hilog日志中附加HiTraceId信息；默认会在hilog日志中附加HiTraceId信息。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## FAILURE_TRIGGER

```TypeScript
FAILURE_TRIGGER = 1 << 5
```

故障触发标志。预置标志，暂未启用。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## D2D_TP_INFO

```TypeScript
D2D_TP_INFO = 1 << 6
```

设备间埋点标志，为TP_INFO的子集，用于调试场景。已设置TP_INFO时，D2D_TP_INFO不生效；未设置TP_INFO时，D2D_TP_INFO生效，调用信息埋点接口 [tracepoint()](arkts-performanceanalysis-hitracechain-tracepoint-f.md)仅在mode参数为DEVICE时打印埋点信息hilog日志。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace
