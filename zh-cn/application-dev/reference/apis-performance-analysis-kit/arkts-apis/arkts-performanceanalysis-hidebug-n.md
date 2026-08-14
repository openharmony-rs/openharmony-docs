# hidebug

为应用提供多种调试、调优的方法，帮助开发者定位性能瓶颈、优化应用性能。主要功能包括：内存数据分析、CPU使用率监控、trace采集、profiler采集、VM堆快照转储。由于该模块的接口大多比较耗费性能，接口调用较为耗时，且基于HiDebug模块定义，该模块内的接口仅建议在应用调试、调优阶段使用。若需要在其他场景使用时，请认真评估所需调用的接口对应用性能的影响。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace hidebug--><!--Device-unnamed-declare namespace hidebug-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [tags](arkts-performanceanalysis-hidebug-tags-n.md) | 支持trace使用场景的标签，用户可通过hitrace抓取指定标签的trace内容。 > **注意** > > 以下标签实际值由系统定义，可能随版本升级而发生改变，为避免升级后出现兼容性问题，在生产中应直接使用标签名称而非标签数值。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [getNativeHeapSize](arkts-performanceanalysis-hidebug-getnativeheapsize-f.md#getNativeHeapSize) | 获取内存分配器统计的进程持有的普通块所占用的总字节数。 |
| [getNativeHeapAllocatedSize](arkts-performanceanalysis-hidebug-getnativeheapallocatedsize-f.md#getNativeHeapAllocatedSize) | 获取内存分配器统计的进程持有的已使用的普通块所占用的总字节数。 |
| [getNativeHeapFreeSize](arkts-performanceanalysis-hidebug-getnativeheapfreesize-f.md#getNativeHeapFreeSize) | 获取内存分配器统计的进程持有的空闲的普通块所占用的总字节数。 |
| [getVss](arkts-performanceanalysis-hidebug-getvss-f.md#getVss) | 获取应用进程占用的虚拟内存大小。接口实现方式：读取/proc/{pid}/statm节点中的size值（内存页数），vss = size * 页大小（4KB/页）。 |
| [getPss](arkts-performanceanalysis-hidebug-getpss-f.md#getPss) | 获取应用进程实际使用的物理内存大小。接口实现方式：读取/proc/{pid}/smaps_rollup节点中的Pss与SwapPss值并求和。 > **注意** > > 由于/proc/{pid}/smaps_rollup的读取耗时较长，建议不要在主线程中使用该接口，可通过@ohos.taskpool或@ohos.worker开启异步线程以避免应用出现卡顿。 |
| [getSharedDirty](arkts-performanceanalysis-hidebug-getshareddirty-f.md#getSharedDirty) | 获取进程的共享脏内存大小。接口实现方式：读取/proc/{pid}/smaps_rollup节点中的Shared_Dirty值。 > **注意** > > 由于/proc/{pid}/smaps_rollup的读取耗时较长，建议不要在主线程中使用该接口，可通过@ohos.taskpool或@ohos.worker开启异步线程以避免应用出现卡顿。 |
| [getPrivateDirty](arkts-performanceanalysis-hidebug-getprivatedirty-f.md#getPrivateDirty) | 获取进程的私有脏内存大小。读取/proc/{pid}/smaps_rollup中的Private_Dirty值。 > **注意** > > 由于/proc/{pid}/smaps_rollup的读取耗时较长，建议不要在主线程中使用该接口，可通过@ohos.taskpool或@ohos.worker开启异步线程以避免应用出现卡顿。 |
| [getCpuUsage](arkts-performanceanalysis-hidebug-getcpuusage-f.md#getCpuUsage) | 获取进程的CPU使用率。 > **注意** > > 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。 |
| [startProfiling](arkts-performanceanalysis-hidebug-startprofiling-f.md#startProfiling) | 启动虚拟机Profiling方法跟踪，`startProfiling(filename: string)`方法的调用需要与`stopProfiling()`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。 |
| [stopProfiling](arkts-performanceanalysis-hidebug-stopprofiling-f.md#stopProfiling) | 停止虚拟机Profiling方法跟踪，`stopProfiling()`方法的调用需要与`startProfiling(filename: string)`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。 |
| [dumpHeapData](arkts-performanceanalysis-hidebug-dumpheapdata-f.md#dumpHeapData) | 虚拟机堆数据转储，生成`filename.heapsnapshot`文件。 |
| [startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md#startJsCpuProfiling) | 启动虚拟机Profiling方法跟踪，`startJsCpuProfiling(filename: string)`方法的调用需要与`stopJsCpuProfiling()`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。 |
| [stopJsCpuProfiling](arkts-performanceanalysis-hidebug-stopjscpuprofiling-f.md#stopJsCpuProfiling) | 停止虚拟机Profiling方法跟踪，`stopJsCpuProfiling()`方法的调用需要与`startJsCpuProfiling(filename: string)`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。 |
| [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md#dumpJsHeapData) | 虚拟机堆数据转储。 > **注意** > > 由于虚拟机堆导出极其耗时，且该接口为同步接口，建议不要在上架版本中调用该接口，以避免应用冻屏，影响用户体验。 |
| [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md#dumpJsHeapData) | 虚拟机堆数据转储，支持清除nodeId缓存。 > **注意** > > 由于虚拟机堆导出极其耗时，且该接口为同步接口，建议不要在上架版本中调用该接口，以避免应用冻屏，影响用户体验。 |
| [getServiceDump](arkts-performanceanalysis-hidebug-getservicedump-f.md#getServiceDump) | 获取系统服务信息。 |
| [getSystemCpuUsage](arkts-performanceanalysis-hidebug-getsystemcpuusage-f.md#getSystemCpuUsage) | 获取系统的CPU资源占用情况。 > **注意** > > 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。 |
| [getAppThreadCpuUsage](arkts-performanceanalysis-hidebug-getappthreadcpuusage-f.md#getAppThreadCpuUsage) | 获取应用线程CPU使用情况。 > **注意** > > 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。 |
| [getSystemMemInfo](arkts-performanceanalysis-hidebug-getsystemmeminfo-f.md#getSystemMemInfo) | 获取系统内存信息。读取/proc/meminfo节点的数据。 |
| [getAppNativeMemInfo](arkts-performanceanalysis-hidebug-getappnativememinfo-f.md#getAppNativeMemInfo) | 获取应用进程内存信息。读取/proc/{pid}/smaps_rollup和/proc/{pid}/statm节点的数据。 > **注意** > > 由于读取/proc/{pid}/smaps_rollup耗时较长，推荐使用异步接口hidebug.getAppNativeMemInfoAsync，以避免应用丢帧或卡顿。 > > 推荐使用hidebug.getRssInfo接口获取应用的rss使用信息。 |
| [getAppMemoryLimit](arkts-performanceanalysis-hidebug-getappmemorylimit-f.md#getAppMemoryLimit) | 获取应用程序进程的内存限制。 |
| [getAppVMMemoryInfo](arkts-performanceanalysis-hidebug-getappvmmemoryinfo-f.md#getAppVMMemoryInfo) | 获取VM内存相关信息。 |
| [getAppVMObjectUsedSize](arkts-performanceanalysis-hidebug-getappvmobjectusedsize-f.md#getAppVMObjectUsedSize) | 获取当前虚拟机中ArkTS对象所占用的内存大小。 |
| [getAppNativeMemInfoAsync](arkts-performanceanalysis-hidebug-getappnativememinfoasync-f.md#getAppNativeMemInfoAsync) | 读取/proc/{pid}/smaps_rollup和/proc/{pid}/statm节点的数据以获取应用进程内存信息，使用Promise异步回调。 |
| [getAppNativeMemInfoWithCache](arkts-performanceanalysis-hidebug-getappnativememinfowithcache-f.md#getAppNativeMemInfoWithCache) | 获取应用进程内存信息。与`getAppNativeMemInfo`接口相比，该接口使用了缓存机制，以提高性能。缓存的有效期为5分钟。 > **注意** > > 由于读取 /proc/{pid}/smaps_rollup 比较耗时，建议不在主线程中使用该接口。可以通过@ohos.taskpool或@ohos.worker开启异步线程，以避免应用卡顿。 |
| [startAppTraceCapture](arkts-performanceanalysis-hidebug-startapptracecapture-f.md#startAppTraceCapture) | 该接口补充了hitrace功能，开发者可通过该接口完成指定范围的trace自动化采集。由于该接口中trace采集过程中消耗的性能与需要采集的范围成正相关，建议开发者在使用该接口前，通过hitrace命令抓取应用的trace日志，从中筛选出所需trace采集的关键范围，以提高该接口性能。 `startAppTraceCapture()`方法的调用需要与`stopAppTraceCapture()`方法的调用一一对应，重复开启trace采集将导致接口调用异常，由于trace采集过程中会消耗较多性能，开发者应在完成采集后及时关闭。 应用调用startAppTraceCapture接口启动采集trace，当采集的trace大小超过了limitSize，系统将自动调用stopAppTraceCapture接口停止采集。因此limitSize大小设置不当，将导致生成trace数据不足，无法满足故障分析。所以要求开发者根据实际情况，评估limitSize大小。 评估方法：limitSize = 预期trace采集时长 * trace单位流量。 预期trace采集时长：开发者根据分析的故障场景自行决定，单位秒。 trace单位流量：应用每秒产生的trace大小，系统推荐值为300KB/s，建议开发者采用自身应用的实测值，单位KB/s。 trace单位流量实测方法：limitSize设置为最大值500M，调用startAppTraceCapture接口，在应用上操作N秒后，调用stopAppTraceCapture停止采集，然后查看trace大小S（KB）。那么trace单位流量 = S/N（KB/s）。 |
| [stopAppTraceCapture](arkts-performanceanalysis-hidebug-stopapptracecapture-f.md#stopAppTraceCapture) | 停止应用trace采集。调用前，需先调用`startAppTraceCapture()`方法开始采集。关闭前未开启或重复关闭会导致接口异常。 调用startAppTraceCapture接口，如果没有合理传入limitSize参数，生成trace的大小大于传入的limitSize大小，系统内部会自动调用stopAppTraceCapture，再次手动调用stopAppTraceCapture就会抛出错误码11400105。 |
| [getGwpAsanGrayscaleState](arkts-performanceanalysis-hidebug-getgwpasangrayscalestate-f.md#getGwpAsanGrayscaleState) | 获取当前GWP-ASan剩余使能天数。 |
| [requestTrace](arkts-performanceanalysis-hidebug-requesttrace-f.md#requestTrace) | 获取当前进程的trace信息，包含应用tag、图像窗口tag、cpu调度和binder内核信息。使用Promise异步回调。 采集trace返回的.sys文件在目录下最多存储3份，数量大于等于3份时再次调用接口会抛出错误码11400120。 |
| [getVMRuntimeStats](arkts-performanceanalysis-hidebug-getvmruntimestats-f.md#getVMRuntimeStats) | 获取系统GC统计信息。 |
| [getVMRuntimeStat](arkts-performanceanalysis-hidebug-getvmruntimestat-f.md#getVMRuntimeStat) | 根据参数获取指定的系统GC统计信息。 |
| [setAppResourceLimit](arkts-performanceanalysis-hidebug-setappresourcelimit-f.md#setAppResourceLimit) | 设置应用的文件描述符数量、线程数量、JS内存或Native内存资源限制。 主要应用场景在于构造内存泄漏故障。 > **注意** > > 打开设置中的开发者选项后，在开发者选项列表中找到"系统资源泄漏日志"并启用，重启设备后接口生效。 |
| [isDebugState](arkts-performanceanalysis-hidebug-isdebugstate-f.md#isDebugState) | 获取应用进程的调试状态。 |
| [getGraphicsMemory](arkts-performanceanalysis-hidebug-getgraphicsmemory-f.md#getGraphicsMemory) | 获取应用显存总大小（gl + graph），使用Promise异步回调。 |
| [getGraphicsMemorySync](arkts-performanceanalysis-hidebug-getgraphicsmemorysync-f.md#getGraphicsMemorySync) | 使用同步方式获取应用显存总大小（gl + graph）。 > **注意** > > 由于该接口涉及多次跨进程通信，其耗时可能达到秒级。为了避免引入性能问题，建议不要在主线程调用该接口，推荐使用异步接口`getGraphicsMemory`。 |
| [getGraphicsMemorySummary](arkts-performanceanalysis-hidebug-getgraphicsmemorysummary-f.md#getGraphicsMemorySummary) | 获取应用显存数据，使用Promise进行异步回调。 |
| [setJsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-setjsrawheaptrimlevel-f.md#setJsRawHeapTrimLevel) | 设置当前进程转储虚拟机原始堆快照的裁剪级别。使用该接口并传入参数TRIM_LEVEL_2，可以有效减少堆快照的文件大小。 > **注意** > > 默认裁剪级别是TRIM_LEVEL_1。如果设置了TRIM_LEVEL_2裁剪，需使用API version 20之后的rawheap-translator工具才能将.rawheap文件转换为.heapsnapshot文件，否则可能导致转换失败。 > > 该接口影响dumpJsRawHeapData的结果。 |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md#dumpJsRawHeapData) | 为当前线程转储虚拟机的原始堆快照，并生成的rawheap格式文件，使用Promise异步回调完成。该文件可通过rawheap-translator工具转化为heapsnapshot格式文件进行解析。 > **注意** > > 系统通过该接口转存快照会消耗大量资源，因此严格限制了调用频率和次数。处理完生成的文件后，请立即删除。 > > 建议在开发者模式下调用该接口，可免除调用配额限制，当设置的开发者选项开关打开并重启设备后即可生效。 |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md#dumpJsRawHeapData) | 为当前线程转储虚拟机的原始堆快照，并支持清除nodeId缓存。生成的文件为rawheap格式，使用Promise异步回调完成。该文件可通过rawheap-translator工具转化为heapsnapshot格式文件进行解析。 > **注意** > > 系统通过该接口转存快照会消耗大量资源，因此严格限制了调用频率和次数。处理完生成的文件后，请立即删除。 > > 建议在开发者模式下调用该接口，可免除调用配额限制，当设置的开发者选项开关打开并重启设备后即可生效。 |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md#dumpJsRawHeapData) | 为当前线程或其所属进程生成虚拟机的原始堆快照，并支持清除nodeId缓存，生成的文件为rawheap格式。使用Promise异步回调。文件可通过rawheap-translator工具转换为heapsnapshot格式文件进行解析。 > **注意** > > 系统通过该接口转储快照会消耗大量资源，因此严格限制了调用频率和次数。处理完生成的文件后，请立即删除。 > > 建议在开发者模式下调用该接口，可免除调用配额限制，当设置的开发者选项开关打开并重启设备后即可生效。 |
| [enableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-enablegwpasangrayscale-f.md#enableGwpAsanGrayscale) | 使能GWP-ASan，用于检测堆内存使用中的非法行为。 该接口主要用于动态配置并启用GWP-ASan，以适配应用自定义的GWP-ASan检测策略。配置在应用重新启动后生效。 |
| [disableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-disablegwpasangrayscale-f.md#disableGwpAsanGrayscale) | 停止使能GWP-ASan。调用该接口将取消自定义配置，恢复默认参数GwpAsanOptions。 |
| [getGwpAsanGrayscaleState](arkts-performanceanalysis-hidebug-getgwpasangrayscalestate-f.md#getGwpAsanGrayscaleState) | 获取当前GWP-ASan剩余使能天数。 |
| [setProcDumpInSharedOOM](arkts-performanceanalysis-hidebug-setprocdumpinsharedoom-f.md#setProcDumpInSharedOOM) | 将转储的堆快照由线程级改为进程级。 > **注意** > > 要想转储进程级的堆快照，调用该接口并传参true、进程OOM时发生的是SharedHeap OOM，两个条件缺一不可。 > > 该接口不影响其他场景下转储的堆快照内容。如：不会影响dumpJsRawHeapData的结果。 > > 该接口在应用的生命周期内可被多次调用，但仅最后一次调用的执行结果会生效。 |
| [getRssInfo](arkts-performanceanalysis-hidebug-getrssinfo-f.md#getRssInfo) | 获取应用程序进程的物理内存使用信息。读取/proc/{pid}/status节点的数据。 > **注意** > > 读取/proc/{pid}/status耗时很短，与hidebug.getAppNativeMemInfo接口中获取的`rss`值相比存在一点误差，但该接口更加轻量，为避免应用丢帧或卡顿推荐使用该接口。 |
| [enableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-enablegwpasangrayscale-f.md#enableGwpAsanGrayscale) | 使能GWP-ASan，用于检测堆内存使用中的非法行为。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ThreadCpuUsage](arkts-performanceanalysis-hidebug-threadcpuusage-i.md) | 线程的CPU使用情况。 |
| [SystemMemInfo](arkts-performanceanalysis-hidebug-systemmeminfo-i.md) | 描述系统内存信息，包括总内存、空闲内存和可用内存。 |
| [NativeMemInfo](arkts-performanceanalysis-hidebug-nativememinfo-i.md) | 描述应用进程的内存信息。 |
| [MemoryLimit](arkts-performanceanalysis-hidebug-memorylimit-i.md) | 应用进程内存限制。 |
| [VMMemoryInfo](arkts-performanceanalysis-hidebug-vmmemoryinfo-i.md) | VM内存信息。 |
| [RequestTraceConfig](arkts-performanceanalysis-hidebug-requesttraceconfig-i.md) | 提供trace采集的参数选项。 |
| [GraphicsMemorySummary](arkts-performanceanalysis-hidebug-graphicsmemorysummary-i.md) | 描述应用显存数据，包括gl和graph部分。 |
| [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | GWP-ASan配置项。可用于配置是否使能、采样频率，以及最大分配的插槽数。 |
| [RssInfo](arkts-performanceanalysis-hidebug-rssinfo-i.md) | 描述应用进程的物理内存信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TraceFlag](arkts-performanceanalysis-hidebug-traceflag-e.md) | 描述采集trace线程的类型，包括主线程和所有线程。 |
| [JsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-jsrawheaptrimlevel-e.md) | 转储堆快照的裁剪级别的枚举。 TRIM_LEVEL_2相比TRIM_LEVEL_1，裁剪时间更长。冻屏的阈值为6秒。使用TRIM_LEVEL_1时，不会达到该阈值；切换至TRIM_LEVEL_2时，裁剪时间可能会超过6秒，触发APP_FREEZE（冻屏事件），导致应用被系统终止，此时回退至TRIM_LEVEL_1级别进行裁剪。 推荐优先使用TRIM_LEVEL_1确保应用稳定，仅在需要更彻底裁剪时尝试TRIM_LEVEL_2。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [GcStats](arkts-performanceanalysis-hidebug-gcstats-t.md) | 描述用于存储GC统计信息的键值对。该类型不支持多线程操作，如果应用中存在多线程同时访问，需加锁保护。 |

