# NativeMemInfo

描述应用进程的内存信息。

**起始版本：** 23

<!--Device-hidebug-interface NativeMemInfo--><!--Device-hidebug-interface NativeMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## privateClean

```TypeScript
privateClean: bigint
```

私有干净内存大小，以KB为单位，计算方式：/proc/{pid}/smaps_rollup: Private_Clean。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-privateClean: bigint--><!--Device-NativeMemInfo-privateClean: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## privateDirty

```TypeScript
privateDirty: bigint
```

私有脏内存大小，以KB为单位，计算方式：/proc/{pid}/smaps_rollup: Private_Dirty。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-privateDirty: bigint--><!--Device-NativeMemInfo-privateDirty: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## pss

```TypeScript
pss: bigint
```

实际占用的物理内存大小(比例分配共享库占用的内存)，以KB为单位，计算方式：/proc/{pid}/smaps_rollup: Pss + SwapPss。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-pss: bigint--><!--Device-NativeMemInfo-pss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## rss

```TypeScript
rss: bigint
```

实际占用的物理内存大小(包括共享库占用)，以KB为单位，计算方式：/proc/{pid}/smaps_rollup: Rss。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-rss: bigint--><!--Device-NativeMemInfo-rss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedClean

```TypeScript
sharedClean: bigint
```

共享净内存大小，以KB为单位，计算方式：/proc/{pid}/smaps_rollup: Shared_Clean。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-sharedClean: bigint--><!--Device-NativeMemInfo-sharedClean: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedDirty

```TypeScript
sharedDirty: bigint
```

共享脏内存大小，以KB为单位，计算方式：/proc/{pid}/smaps_rollup: Shared_Dirty。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-sharedDirty: bigint--><!--Device-NativeMemInfo-sharedDirty: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vss

```TypeScript
vss: bigint
```

占用的虚拟内存大小(包括共享库所占用的内存)，以KB为单位，计算方式：/proc/{pid}/statm: size * 4。

**类型：** bigint

**起始版本：** 23

<!--Device-NativeMemInfo-vss: bigint--><!--Device-NativeMemInfo-vss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

