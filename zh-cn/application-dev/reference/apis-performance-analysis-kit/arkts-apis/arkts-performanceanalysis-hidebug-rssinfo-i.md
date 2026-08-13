# RssInfo

描述应用进程的物理内存信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-hidebug-interface RssInfo--><!--Device-hidebug-interface RssInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## rss

```TypeScript
rss: bigint
```

实际占用的物理内存大小（Resident Set Size），包含匿名页、文件映射页和共享内存页，以KB为单位，计算方式：/proc/{pid}/status: VmRss。

**类型：** bigint

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RssInfo-rss: bigint--><!--Device-RssInfo-rss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## swapRss

```TypeScript
swapRss: bigint
```

换出到交换分区的匿名私有页总大小，以KB为单位，计算方式：/proc/{pid}/status: VmSwap。

**类型：** bigint

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RssInfo-swapRss: bigint--><!--Device-RssInfo-swapRss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

