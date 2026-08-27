# SystemMemInfo

描述系统内存信息，包括总内存、空闲内存和可用内存。

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
```

## availableMem

```TypeScript
availableMem: bigint
```

系统可用的内存，以KB为单位，计算方式：/proc/meminfo: MemAvailable

**类型：** bigint

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## freeMem

```TypeScript
freeMem: bigint
```

系统空闲的内存，以KB为单位，计算方式：/proc/meminfo: MemFree

**类型：** bigint

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## totalMem

```TypeScript
totalMem: bigint
```

系统总的内存，以KB为单位，计算方式：/proc/meminfo: MemTotal

**类型：** bigint

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
