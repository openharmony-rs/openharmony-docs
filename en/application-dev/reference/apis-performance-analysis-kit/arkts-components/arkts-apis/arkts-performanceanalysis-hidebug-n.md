# hidebug

HiDebug provides multiple methods for debugging and profiling applications. With these methods, you can obtain memory, CPU, GPU, and GC data, collect process trace and profiler data, and dump VM heap snapshots. Since most APIs of this module are both performance-consuming and time-consuming, and are defined based on the HiDebug module, you are advised to use these APIs only during the application debugging and profiling phases. If the APIs are required in other scenarios, evaluate the impact of the APIs on application performance.

@namespace hidebug

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [tags](arkts-performanceanalysis-hidebug-tags-n.md) | Provide trace tags |

### Functions

| Name | Description |
| --- | --- |
| [getNativeHeapSize](arkts-performanceanalysis-hidebug-getnativeheapsize-f.md) | Obtains the total number of bytes occupied by the total space (**uordblks** + **fordblks**, which are obtained from **mallinfo**) held by a process, which is measured by the memory allocator. |
| [getNativeHeapAllocatedSize](arkts-performanceanalysis-hidebug-getnativeheapallocatedsize-f.md) | Obtains the total number of bytes occupied by the total allocated space (**uordblks**, which is obtained from **mallinfo**) held by a process, which is measured by the memory allocator. |
| [getNativeHeapFreeSize](arkts-performanceanalysis-hidebug-getnativeheapfreesize-f.md) | Obtains the total number of bytes occupied by the total free space (**fordblks**, which is obtained from **mallinfo**) held by a process, which is measured by the memory allocator. |
| [getVss](arkts-performanceanalysis-hidebug-getvss-f.md) | Obtains the virtual set size used by the application process. This API is implemented by multiplying the value of **size** (number of memory pages) in the **\/proc/{pid}/statm** node by the page size (4 KB per page). |
| [getPss](arkts-performanceanalysis-hidebug-getpss-f.md) | Obtains the size of the physical memory actually used by the application process. This API is implemented by summing up the values of **Pss** and **SwapPss** in the **\/proc/{pid}/smaps_rollup** node. |
| [getSharedDirty](arkts-performanceanalysis-hidebug-getshareddirty-f.md) | Obtains the size of the shared dirty memory of a process. This API is implemented by reading the value of **Shared_Dirty** in the **\/proc/{pid}/smaps_rollup** node. |
| [getPrivateDirty](arkts-performanceanalysis-hidebug-getprivatedirty-f.md) | Obtains the size of the private dirty memory of a process. This API is implemented by reading the value of **Private_Dirty** in the **\/proc/{pid}/smaps_rollup** node. |
| [getCpuUsage](arkts-performanceanalysis-hidebug-getcpuusage-f.md) | Obtains the CPU usage of a process. |
| [startProfiling](arkts-performanceanalysis-hidebug-startprofiling-f.md) | Starts the VM profiling method. **startProfiling(filename: string)** and **stopProfiling()** are called in pairs. **startProfiling(filename: string)** always occurs before **stopProfiling()**. You are advised not to call either of these methods repeatedly. Otherwise, an exception may occur. |
| [stopProfiling](arkts-performanceanalysis-hidebug-stopprofiling-f.md) | Stops the VM profiling method. **stopProfiling()** and **startProfiling(filename: string)** are called in pairs. **startProfiling(filename: string)** always occurs before **stopProfiling()**. You are advised not to call either of these methods repeatedly. Otherwise, an exception may occur. |
| [dumpHeapData](arkts-performanceanalysis-hidebug-dumpheapdata-f.md) | Dumps the VM heap data and generates the **filename.heapsnapshot** file. |
| [startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md) | Starts the VM profiling method. **startJsCpuProfiling(filename: string)** and **stopJsCpuProfiling()** are called in pairs. **startJsCpuProfiling(filename: string)** always occurs before **stopJsCpuProfiling()**. You are advised not to call either of these methods repeatedly. Otherwise, an exception may occur. |
| [stopJsCpuProfiling](arkts-performanceanalysis-hidebug-stopjscpuprofiling-f.md) | Stops the VM profiling method. **stopJsCpuProfiling()** and **startJsCpuProfiling(filename: string)** are called in pairs. **startJsCpuProfiling()** always occurs before **stopJsCpuProfiling()**. You are advised not to call either of these methods repeatedly. Otherwise, an exception may occur. |
| [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md) | Dumps VM heap data. |
| [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md) | Dumps VM heap data and clears the nodeId cache. |
| [getServiceDump](arkts-performanceanalysis-hidebug-getservicedump-f.md) | Obtains system service information. |
| [getSystemCpuUsage](arkts-performanceanalysis-hidebug-getsystemcpuusage-f.md) | Obtains the CPU usage of the system. |
| [getAppThreadCpuUsage](arkts-performanceanalysis-hidebug-getappthreadcpuusage-f.md) | Obtains the CPU usage of application threads. |
| [getSystemMemInfo](arkts-performanceanalysis-hidebug-getsystemmeminfo-f.md) | Obtains system memory information. This API is implemented by reading data from the **\/proc/meminfo** node. |
| [getAppNativeMemInfo](arkts-performanceanalysis-hidebug-getappnativememinfo-f.md) | Obtains the memory information of the application process. This API is implemented by reading data from the **\/proc/{pid}/smaps_rollup and /proc/{pid}/statm** node. |
| [getAppMemoryLimit](arkts-performanceanalysis-hidebug-getappmemorylimit-f.md) | Obtains the memory limit of an application process. |
| [getAppVMMemoryInfo](arkts-performanceanalysis-hidebug-getappvmmemoryinfo-f.md) | Obtains VM memory information. |
| [getAppVMObjectUsedSize](arkts-performanceanalysis-hidebug-getappvmobjectusedsize-f.md) | Obtains the VM memory size occupied by ArkTS objects. |
| [getAppNativeMemInfoAsync](arkts-performanceanalysis-hidebug-getappnativememinfoasync-f.md) | Obtains the memory information of application processes by reading the data of the **\/proc/{pid}/smaps_rollup** and **\/proc/{pid}/statm** nodes. This API uses a promise to return the result. |
| [getAppNativeMemInfoWithCache](arkts-performanceanalysis-hidebug-getappnativememinfowithcache-f.md) | Obtains the memory information of the application process. This API uses the cache mechanism and has higher performance than the **getAppNativeMemInfo** API. The cache is valid for 5 minutes. |
| [startAppTraceCapture](arkts-performanceanalysis-hidebug-startapptracecapture-f.md) | Starts automatic trace collection in a specified scope. This API is a supplement to the HiTrace module. The performance consumption during trace collection increases with the collection scope. Therefore, before using this API, you are advised to run the **hitrace** command to capture trace logs and select the key scope of trace collection to improve the API performance. |
| [stopAppTraceCapture](arkts-performanceanalysis-hidebug-stopapptracecapture-f.md) | Stops application trace collection. Use [startAppTraceCapture()](arkts-performanceanalysis-hidebug-startapptracecapture-f.md) to start collection before calling this API. If this API is called before trace collection or it is repeatedly called, an exception will occur. |
| [requestTrace](arkts-performanceanalysis-hidebug-requesttrace-f.md) | Obtains the trace information of the current process, including the application tag, image window tag, CPU scheduling, and binder kernel information. This API uses a promise to return the result. |
| [getVMRuntimeStats](arkts-performanceanalysis-hidebug-getvmruntimestats-f.md) | Obtains the system GC statistics. |
| [getVMRuntimeStat](arkts-performanceanalysis-hidebug-getvmruntimestat-f.md) | Obtains the specified system GC statistics based on parameters. |
| [setAppResourceLimit](arkts-performanceanalysis-hidebug-setappresourcelimit-f.md) | Sets the number of FDs, number of threads, JS memory, or native memory limit of the application. |
| [isDebugState](arkts-performanceanalysis-hidebug-isdebugstate-f.md) | Obtains the debugging state of an application process. |
| [getGraphicsMemory](arkts-performanceanalysis-hidebug-getgraphicsmemory-f.md) | Obtains the total GPU memory size (**gl** + **graph**) of the application. This API uses a promise to return the result. |
| [getGraphicsMemorySync](arkts-performanceanalysis-hidebug-getgraphicsmemorysync-f.md) | Obtains the total GPU memory size (GL + graph) of an application in synchronous mode. |
| [getGraphicsMemorySummary](arkts-performanceanalysis-hidebug-getgraphicsmemorysummary-f.md) | Obtains the GPU memory data of an application. This API uses a promise to return the result. |
| [setJsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-setjsrawheaptrimlevel-f.md) | Sets the trimming level of the original heap snapshot stored by the current process. Using **TRIM_LEVEL_2** for this API can effectively reduce the size of the heap snapshot file. |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md) | Dumps the original heap snapshot of the VM for the current thread and generates a .rawheap file. This API uses a promise to return the result. The file can be converted into a heapsnapshot file using rawheap-translator for parsing. |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md) | Dumps the original heap snapshot of the VM for the current thread and clears the **nodeId** cache. The generated file is in the rawheap format. This API uses a promise to return the result. The file can be converted into a heapsnapshot file using rawheap-translator for parsing. |
| [dumpJsRawHeapData](arkts-performanceanalysis-hidebug-dumpjsrawheapdata-f.md) | Dumps the original heap snapshot of the VM for the current thread or the process to which the current thread belongs, clears the nodeId cache, and generates a .rawheap file. This API uses a promise to return the result. The file can be converted into a heapsnapshot file using rawheap-translator for parsing. |
| [enableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-enablegwpasangrayscale-f.md) | Enables GWP-ASan to detect illegal behaviors in heap memory usage. |
| [disableGwpAsanGrayscale](arkts-performanceanalysis-hidebug-disablegwpasangrayscale-f.md) | Disables GWP-ASan. This API is used to cancel the custom configuration and restore the default parameter [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md). |
| [getGwpAsanGrayscaleState](arkts-performanceanalysis-hidebug-getgwpasangrayscalestate-f.md) | Obtains the number of remaining days for enabling GWP-ASan. |
| [setProcDumpInSharedOOM](arkts-performanceanalysis-hidebug-setprocdumpinsharedoom-f.md) | Changes the dump heap snapshot from the thread-level to the process-level. |
| [getRssInfo](arkts-performanceanalysis-hidebug-getrssinfo-f.md) | Obtains the physical memory usage of the application process. Reads data from the **\/proc/{pid}/status** node. |
| [getAppRunningUniqueId](arkts-performanceanalysis-hidebug-getapprunninguniqueid-f.md) | Obtains the running unique identifier of the application. |

### Interfaces

| Name | Description |
| --- | --- |
| [ThreadCpuUsage](arkts-performanceanalysis-hidebug-threadcpuusage-i.md) | Describes the CPU usage of a thread. |
| [SystemMemInfo](arkts-performanceanalysis-hidebug-systemmeminfo-i.md) | Describes the system memory information, including the total memory, free memory, and available memory. |
| [NativeMemInfo](arkts-performanceanalysis-hidebug-nativememinfo-i.md) | Describes memory information of the application process. |
| [MemoryLimit](arkts-performanceanalysis-hidebug-memorylimit-i.md) | Defines the memory limit of the application process. |
| [VMMemoryInfo](arkts-performanceanalysis-hidebug-vmmemoryinfo-i.md) | Describes the VM memory information. |
| [RequestTraceConfig](arkts-performanceanalysis-hidebug-requesttraceconfig-i.md) | Provides options of trace collection. |
| [GraphicsMemorySummary](arkts-performanceanalysis-hidebug-graphicsmemorysummary-i.md) | Describes the GPU memory data of an application, including the GL and Graph parts. |
| [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | Enumerates the GWP-ASan configuration items. You can configure whether to enable GWP-Asan, the sampling frequency, and the maximum number of allocated slots. |
| [RssInfo](arkts-performanceanalysis-hidebug-rssinfo-i.md) | Describes the physical memory information about an application process. |

### Types

| Name | Description |
| --- | --- |
| [GcStats](arkts-performanceanalysis-hidebug-gcstats-t.md) | Describes the key-value pair used to store GC statistics. This type does not support multi-thread operations. If this type is operated by multiple threads at the same time in an application, use a lock for it. |

### Enums

| Name | Description |
| --- | --- |
| [TraceFlag](arkts-performanceanalysis-hidebug-traceflag-e.md) | Describes types of trace collection threads, including the main thread and all threads. |
| [JsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-jsrawheaptrimlevel-e.md) | Enumerates the trimming levels of the heap snapshot. |
