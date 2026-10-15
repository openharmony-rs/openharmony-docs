# hidebug

```TypeScript
declare namespace hidebug
```

为应用提供多种调试、调优的方法，帮助开发者定位性能瓶颈、优化应用性能。主要功能包括：内存数据分析、CPU使用率监控、trace采集、profiler采集、VM堆快照转储。由于该模块的接口大多比较耗费性能，接口调用较为耗时，且基于HiDebug模块定义，该模块内的接口仅建议在应用调试、调优阶段使用。若需要在其他场景使用时，请认真评估所需调用的接口对应用性能的影响。

@namespace hidebug

**起始版本：** 8

<!--Device-unnamed-declare namespace hidebug--><!--Device-unnamed-declare namespace hidebug-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [tags](arkts-performanceanalysis-hidebug-tags-n.md) |  |

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-disablegwpasangrayscale-f.md#disablegwpasangrayscale) | 停止使能GWP-ASan。调用该接口将取消自定义配置，恢复默认参数[GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md)。 |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md#dumpjsrawheapdata1) | 为当前线程转储虚拟机的原始堆快照，并生成的rawheap格式文件，使用Promise异步回调完成。该文件可通过rawheap-translator工具转化为heapsnapshot格式文件进行解析。 |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md#dumpjsrawheapdata2) | 为当前线程转储虚拟机的原始堆快照，并支持清除nodeId缓存。生成的文件为rawheap格式，使用Promise异步回调完成。该文件可通过rawheap-translator工具转化为heapsnapshot格式文件进行解析。 |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md#dumpjsrawheapdata3) | 为当前线程或其所属进程生成虚拟机的原始堆快照，并支持清除nodeId缓存，生成的文件为rawheap格式。使用Promise异步回调。文件可通过rawheap-translator工具转换为heapsnapshot格式文件进行解析。 |
| [enableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-enablegwpasangrayscale-f.md#enablegwpasangrayscale) | 使能GWP-ASan，用于检测堆内存使用中的非法行为。 |
| [getAppMemoryLimit](arkts-performanceanalysis-hidebug-getappmemorylimit-f.md#getappmemorylimit) | 获取应用程序进程的内存限制。 |
| [getAppNativeMemInfo](arkts-performanceanalysis-hidebug-getappnativememinfo-f.md#getappnativememinfo) | 获取应用进程内存信息。读取/proc/{pid}/smaps_rollup和/proc/{pid}/statm节点的数据。 |
| [getAppNativeMemInfoAsync](arkts-performanceanalysis-hidebug-getappnativememinfoasync-f.md#getappnativememinfoasync) | 读取/proc/{pid}/smaps_rollup和/proc/{pid}/statm节点的数据以获取应用进程内存信息，使用Promise异步回调。 |
| [getAppNativeMemInfoWithCache](arkts-performanceanalysis-hidebug-getappnativememinfowithcache-f.md#getappnativememinfowithcache) | 获取应用进程内存信息。与`getAppNativeMemInfo`接口相比，该接口使用了缓存机制，以提高性能。缓存的有效期为5分钟。 |
| [getAppRunningUniqueId](arkts-performanceanalysis-hidebug-getapprunninguniqueid-f.md#getapprunninguniqueid) | 获取应用程序的运行唯一标识符。 |
| [getAppThreadCpuUsage](arkts-performanceanalysis-hidebug-getappthreadcpuusage-f.md#getappthreadcpuusage) | 获取应用线程CPU使用情况。 |
| [getAppVMMemoryInfo](arkts-performanceanalysis-hidebug-getappvmmemoryinfo-f.md#getappvmmemoryinfo) | 获取VM内存相关信息。 |
| [getAppVMObjectUsedSize](arkts-performanceanalysis-hidebug-getappvmobjectusedsize-f.md#getappvmobjectusedsize) | 获取当前虚拟机中ArkTS对象所占用的内存大小。 |
| [getCpuUsage](arkts-performanceanalysis-hidebug-getcpuusage-f.md#getcpuusage) | 获取进程的CPU使用率。 |
| [getGraphicsMemory](arkts-performanceanalysis-hidebug-getgraphicsmemory-f.md#getgraphicsmemory) | 获取应用显存总大小（gl + graph），使用Promise异步回调。 |
| [getGraphicsMemorySummary](arkts-performanceanalysis-hidebug-getgraphicsmemorysummary-f.md#getgraphicsmemorysummary) | 获取应用显存数据，使用Promise进行异步回调。 |
| [getGraphicsMemorySync](arkts-performanceanalysis-hidebug-getgraphicsmemorysync-f.md#getgraphicsmemorysync) | 使用同步方式获取应用显存总大小（gl + graph）。 |
| [getGwpAsanGrayscaleState](arkts-performanceanalysis-hidebug-getgwpasangrayscalestate-f.md#getgwpasangrayscalestate) | 获取当前GWP-ASan剩余使能天数。 |
| [getNativeHeapAllocatedSize](arkts-performanceanalysis-hidebug-getnativeheapallocatedsize-f.md#getnativeheapallocatedsize) | 获取内存分配器统计的进程持有的已使用的普通块所占用的总字节数。 |
| [getNativeHeapFreeSize](arkts-performanceanalysis-hidebug-getnativeheapfreesize-f.md#getnativeheapfreesize) | 获取内存分配器统计的进程持有的空闲的普通块所占用的总字节数。 |
| [getNativeHeapSize](arkts-performanceanalysis-hidebug-getnativeheapsize-f.md#getnativeheapsize) | 获取内存分配器统计的进程持有的普通块所占用的总字节数。 |
| [getPrivateDirty](arkts-performanceanalysis-hidebug-getprivatedirty-f.md#getprivatedirty) | 获取进程的私有脏内存大小。读取/proc/{pid}/smaps_rollup中的Private_Dirty值。 |
| [getPss](arkts-performanceanalysis-hidebug-getpss-f.md#getpss) | 获取应用进程实际使用的物理内存大小。接口实现方式：读取/proc/{pid}/smaps_rollup节点中的Pss与SwapPss值并求和。 |
| [getRssInfo](arkts-performanceanalysis-hidebug-getrssinfo-f.md#getrssinfo) | 获取应用程序进程的物理内存使用信息。读取/proc/{pid}/status节点的数据。 |
| [getServiceDump](arkts-performanceanalysis-hidebug-getservicedump-f.md#getservicedump) | 获取系统服务信息。 |
| [getSharedDirty](arkts-performanceanalysis-hidebug-getshareddirty-f.md#getshareddirty) | 获取进程的共享脏内存大小。接口实现方式：读取/proc/{pid}/smaps_rollup节点中的Shared_Dirty值。 |
| [getSystemCpuUsage](arkts-performanceanalysis-hidebug-getsystemcpuusage-f.md#getsystemcpuusage) | 获取系统的CPU资源占用情况。 |
| [getSystemMemInfo](arkts-performanceanalysis-hidebug-getsystemmeminfo-f.md#getsystemmeminfo) | 获取系统内存信息。读取/proc/meminfo节点的数据。 |
| [getVMRuntimeStat](arkts-performanceanalysis-hidebug-getvmruntimestat-f.md#getvmruntimestat) | 根据参数获取指定的系统GC统计信息。 |
| [getVMRuntimeStats](arkts-performanceanalysis-hidebug-getvmruntimestats-f.md#getvmruntimestats) | 获取系统GC统计信息。 |
| [getVss](arkts-performanceanalysis-hidebug-getvss-f.md#getvss) | 获取应用进程占用的虚拟内存大小。接口实现方式：读取/proc/{pid}/statm节点中的size值（内存页数），vss = size * 页大小（4KB/页）。 |
| [isDebugState](arkts-performanceanalysis-hidebug-isdebugstate-f.md#isdebugstate) | 获取应用进程的调试状态。 |
| [requestTrace](arkts-performanceanalysis-hidebug-requesttrace-f.md#requesttrace) | 获取当前进程的trace信息，包含应用tag、图像窗口tag、cpu调度和binder内核信息。使用Promise异步回调。 |
| [setAppResourceLimit](arkts-performanceanalysis-hidebug-setappresourcelimit-f.md#setappresourcelimit) | 设置应用的文件描述符数量、线程数量、JS内存或Native内存资源限制。 |
| [setJsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-setjsrawheaptrimlevel-f.md#setjsrawheaptrimlevel) | 设置当前进程转储虚拟机原始堆快照的裁剪级别。使用该接口并传入参数TRIM_LEVEL_2，可以有效减少堆快照的文件大小。 |
| [setProcDumpInSharedOOM](arkts-performanceanalysis-hidebug-setprocdumpinsharedoom-f.md#setprocdumpinsharedoom) | 将转储的堆快照由线程级改为进程级。 |
| [startAppTraceCapture](arkts-performanceanalysis-hidebug-startapptracecapture-f.md#startapptracecapture) | 该接口补充了hitrace功能，开发者可通过该接口完成指定范围的trace自动化采集。由于该接口中trace采集过程中消耗的性能与需要采集的范围成正相关，建议开发者在使用该接口前，通过hitrace命令抓取应用的trace日志，从中筛选出所需trace采集的关键范围，以提高该接口性能。 |
| [startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md#startjscpuprofiling) | 启动虚拟机Profiling方法跟踪，`startJsCpuProfiling(filename: string)`方法的调用需要与`stopJsCpuProfiling()`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。 |
| [stopAppTraceCapture](arkts-performanceanalysis-hidebug-stopapptracecapture-f.md#stopapptracecapture) | 停止应用trace采集。调用前，需先调用'[startAppTraceCapture()](arkts-performanceanalysis-hidebug-startapptracecapture-f.md)'方法开始采集。关闭前未开启或重复关闭会导致接口异常。 |
| [stopJsCpuProfiling](arkts-performanceanalysis-hidebug-stopjscpuprofiling-f.md#stopjscpuprofiling) | 停止虚拟机Profiling方法跟踪，`stopJsCpuProfiling()`方法的调用需要与`startJsCpuProfiling(filename: string)`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。 |
| [dumpHeapData](arkts-performanceanalysis-hidebug-dumpheapdata-f.md#dumpheapdata) |  |
| [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md#dumpjsheapdata1) | 虚拟机堆数据转储。 |
| [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md#dumpjsheapdata2) | 虚拟机堆数据转储，支持清除nodeId缓存。 |
| [startProfiling](arkts-performanceanalysis-hidebug-startprofiling-f.md#startprofiling) |  |
| [stopProfiling](arkts-performanceanalysis-hidebug-stopprofiling-f.md#stopprofiling) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GraphicsMemorySummary](arkts-performanceanalysis-hidebug-graphicsmemorysummary-i.md) | 描述应用显存数据，包括gl和graph部分。 |
| [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | GWP-ASan配置项。可用于配置是否使能、采样频率，以及最大分配的插槽数。 |
| [MemoryLimit](arkts-performanceanalysis-hidebug-memorylimit-i.md) | 应用进程内存限制。 |
| [NativeMemInfo](arkts-performanceanalysis-hidebug-nativememinfo-i.md) | 描述应用进程的内存信息。 |
| [RequestTraceConfig](arkts-performanceanalysis-hidebug-requesttraceconfig-i.md) | 提供trace采集的参数选项。 |
| [RssInfo](arkts-performanceanalysis-hidebug-rssinfo-i.md) | 描述应用进程的物理内存信息。 |
| [SystemMemInfo](arkts-performanceanalysis-hidebug-systemmeminfo-i.md) | 描述系统内存信息，包括总内存、空闲内存和可用内存。 |
| [ThreadCpuUsage](arkts-performanceanalysis-hidebug-threadcpuusage-i.md) | 线程的CPU使用情况。 |
| [VMMemoryInfo](arkts-performanceanalysis-hidebug-vmmemoryinfo-i.md) | VM内存信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [GcStats](arkts-performanceanalysis-hidebug-gcstats-t.md) | 描述用于存储GC统计信息的键值对。该类型不支持多线程操作，如果应用中存在多线程同时访问，需加锁保护。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [JsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-jsrawheaptrimlevel-e.md) | 转储堆快照的裁剪级别的枚举。 |
| [TraceFlag](arkts-performanceanalysis-hidebug-traceflag-e.md) | 描述采集trace线程的类型，包括主线程和所有线程。 |
