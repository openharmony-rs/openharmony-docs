# jsLeakWatcherNative（This module provides the native implementation interfaces of jsLeakWatcher.）

```TypeScript
declare namespace jsLeakWatcherNative
```

提供jsleakwatcher依赖的native能力的封装

这些接口是内部实现细节，暴露为仅系统API。第三方不应该直接调用它们

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace jsLeakWatcherNative--><!--Device-unnamed-declare namespace jsLeakWatcherNative-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [apiRecord](arkts-performanceanalysis-jsleakwatchernative-apirecord-f-sys.md#apirecord-1) | 上报API打点 |
| [dumpRawHeap](arkts-performanceanalysis-jsleakwatchernative-dumprawheap-f-sys.md#dumprawheap-1) | 异步导出堆快照到给定的文件路径。 |
| [dumpRawHeapSync](arkts-performanceanalysis-jsleakwatchernative-dumprawheapsync-f-sys.md#dumprawheapsync-1) | 同步导出ArkTS堆快照。 |
| [getDumpStatus](arkts-performanceanalysis-jsleakwatchernative-getdumpstatus-f-sys.md#getdumpstatus-1) | 获取状态参数，决定是否要自动执行jsleakwatcher的检测。 |
| [handleDumpTask](arkts-performanceanalysis-jsleakwatchernative-handledumptask-f-sys.md#handledumptask-1) | 设置导出任务的回调。在GC之后，如果确定有泄漏，则执行传入的回调。 |
| [handleGCTask](arkts-performanceanalysis-jsleakwatchernative-handlegctask-f-sys.md#handlegctask-1) | 触发并启动周期性GC任务。当期限到期时，自动触发传入的调用。 |
| [handleShutdownTask](arkts-performanceanalysis-jsleakwatchernative-handleshutdowntask-f-sys.md#handleshutdowntask-1) | 注册停止jsleakwatcher任务回调。 |
| [registerArkUIObjectLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-registerarkuiobjectlifecyclecallback-f-sys.md#registerarkuiobjectlifecyclecallback-1) | 注册ArkUI对象生命周期的回调 |
| [registerWindowLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-registerwindowlifecyclecallback-f-sys.md#registerwindowlifecyclecallback-1) | 注册窗口生命周期的回调 |
| [removeTask](arkts-performanceanalysis-jsleakwatchernative-removetask-f-sys.md#removetask-1) | 停止周期性GC和dump任务循环。 |
| [reportRawHeap](arkts-performanceanalysis-jsleakwatchernative-reportrawheap-f-sys.md#reportrawheap-1) | 上报快照导出的结果。 |
| [setDumpDelay](arkts-performanceanalysis-jsleakwatchernative-setdumpdelay-f-sys.md#setdumpdelay-1) | 设置GC后执行dump之前的延迟时间，单位为毫秒。 |
| [setGcDelay](arkts-performanceanalysis-jsleakwatchernative-setgcdelay-f-sys.md#setgcdelay-1) | 设置每轮GC之间的时间间隔，单位为毫秒。 |
| [unregisterArkUIObjectLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-unregisterarkuiobjectlifecyclecallback-f-sys.md#unregisterarkuiobjectlifecyclecallback-1) | 取消注册ArkUI对象生命周期回调 |
| [unregisterWindowLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-unregisterwindowlifecyclecallback-f-sys.md#unregisterwindowlifecyclecallback-1) | 取消注册窗口生命周期回调 |
<!--DelEnd-->
