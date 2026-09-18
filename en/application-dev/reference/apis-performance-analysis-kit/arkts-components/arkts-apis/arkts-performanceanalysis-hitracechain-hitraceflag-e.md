# HiTraceFlag

Enumerates trace flag types.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default flag.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## INCLUDE_ASYNC

```TypeScript
INCLUDE_ASYNC = 1
```

Asynchronous call flag.

When this flag is set, both synchronous and asynchronous calls are traced. By default, only synchronous calls are traced.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## DONOT_CREATE_SPAN

```TypeScript
DONOT_CREATE_SPAN = 1 << 1
```

No span flag.

When this flag is set, no span information is created. By default, span information is created.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## TP_INFO

```TypeScript
TP_INFO = 1 << 2
```

Trace point flag.

When this flag is set in the debugging scenario, the HiLog logs of the trace point are printed upon calling the **[tracepoint()](arkts-performanceanalysis-hitracechain-tracepoint-f.md)** API. By default, the HiLog logs are not printed.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## NO_BE_INFO

```TypeScript
NO_BE_INFO = 1 << 3
```

No begin and end flag.

When this flag is set in the debugging scenario, the HiLog logs about the begin and end of tracing are printed when the [begin()](arkts-performanceanalysis-hitracechain-begin-f.md) and [end()](arkts-performanceanalysis-hitracechain-end-f.md) APIs are called. By default, the HiLog logs about the begin and end of tracing are not printed.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## DISABLE_LOG

```TypeScript
DISABLE_LOG = 1 << 4
```

Log association flag.

When this flag is set, the **HiTraceId** information is not added to the HiLog logs. By default, the **HiTraceId** information is added to the HiLog logs.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## FAILURE_TRIGGER

```TypeScript
FAILURE_TRIGGER = 1 << 5
```

Failure trigger flag. This is a reserved flag.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## D2D_TP_INFO

```TypeScript
D2D_TP_INFO = 1 << 6
```

Device-to-device trace point flag. It is a subset of **TP_INFO** and is used in debugging scenarios.

When the **TP_INFO** flag is set, the **D2D_TP_INFO** flag does not take effect.

When **TP_INFO** is not set and **D2D_TP_INFO** is set, the HiLog logs of the trace point are printed only when the mode parameter is set to **DEVICE** upon calling [tracepoint()](arkts-performanceanalysis-hitracechain-tracepoint-f.md).

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace
