# GwpAsanOptions

Enumerates the GWP-ASan configuration items. You can configure whether to enable GWP-Asan, the sampling frequency, and the maximum number of allocated slots.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## alwaysEnabled

```TypeScript
alwaysEnabled?: boolean
```

The value **true** means to enable GWP-ASan 100%.

The value **false** means to enable GWP-ASan at a probability of 1/128.

The default value is **false**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## isRecover

```TypeScript
isRecover?: boolean
```

Used to control whether applications run in recoverable mode when the probability of enabling GWP-ASan is 100%.

**true**: When GWP-ASan is enabled with a 100% probability, applications run in recoverable mode. In this mode, after the system detects an out-of-bounds address fault, the process will not crash due to the detection mechanism. However, for errors that have caused invalid memory access, the application may still crash.

**false**: When GWP-ASan is enabled with a 100% probability, applications run in unrecoverable mode.

The default value is **false**.

**Note:**  This parameter takes effect only when GWP-ASan is enabled with a 100% probability. When GWP-ASan is enabled with a 1/128 probability, the recoverable mode is used by default and is not controlled by **isRecover**.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxSimutaneousAllocations

```TypeScript
maxSimutaneousAllocations?: number
```

Maximum number of allocated slots. The default value is **1000**. The value must be a positive integer greater than 0. If the value is a decimal, it is rounded up.

When the slots are used up, the newly allocated memory is no longer monitored.

After the used memory is released, the slots occupied by the memory are automatically reused to facilitate subsequent memory monitoring.

You are advised to set this parameter to a value less than or equal to 20000. If the value is too large, the VMA may break down.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sampleRate

```TypeScript
sampleRate?: number
```

Sampling rate of GWP-ASan. The default value is **2500**. The value must be a positive integer greater than 0. If the value is a decimal, it is rounded up.

GWP-Asan performs sampling on the allocated memory at a probability of 1/**sampleRate**.

You are advised to set this parameter to a value greater than or equal to 1000. If the value is too small, the performance is affected.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
