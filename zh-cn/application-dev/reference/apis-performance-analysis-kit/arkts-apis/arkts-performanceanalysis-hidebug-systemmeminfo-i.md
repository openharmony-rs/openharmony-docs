# SystemMemInfo

描述系统内存信息，包括总内存、空闲内存和可用内存。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-interface SystemMemInfo--><!--Device-hidebug-interface SystemMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## availableMem

```TypeScript
availableMem: bigint
```

系统可用的内存，以KB为单位，计算方式：/proc/meminfo: MemAvailable。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemMemInfo-availableMem: bigint--><!--Device-SystemMemInfo-availableMem: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## freeMem

```TypeScript
freeMem: bigint
```

系统空闲的内存，以KB为单位，计算方式：/proc/meminfo: MemFree。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemMemInfo-freeMem: bigint--><!--Device-SystemMemInfo-freeMem: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## totalMem

```TypeScript
totalMem: bigint
```

系统总的内存，以KB为单位，计算方式：/proc/meminfo: MemTotal。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemMemInfo-totalMem: bigint--><!--Device-SystemMemInfo-totalMem: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

