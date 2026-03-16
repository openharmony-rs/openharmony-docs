# 应用终止事件介绍

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @xuxinao-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

## 概述

从API version 20开始，HiAppEvent提供接口用于订阅应用终止事件。

应用终止是指应用程序被系统强制退出的一种现象。与应用崩溃不同，终止并非源于应用自身业务代码的异常，而是主要归因于系统基于资源管控策略而对应用实施的终止行为。

HiAppEvent提供接口用于订阅应用终止事件。

- [订阅应用终止事件（ArkTS）](hiappevent-watcher-app-killed-events-arkts.md)
- [订阅应用终止事件（C/C++）](hiappevent-watcher-app-killed-events-ndk.md)

> **说明：**
>
> 应用终止事件支持在[应用分身](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/app-clone)场景下使用 HiAppEvent 进行订阅，支持在原子化服务场景下使用 HiAppEvent 进行订阅，从 API version 22 开始支持在[输入法应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/inputmethod-application-guide)场景下使用 HiAppEvent 进行订阅。

应用终止事件信息中params属性的详细描述如下：

## 事件字段说明

### params字段说明

终止事件信息中params属性的详细描述如下：

| 名称    | 类型   | 说明                       |
| ------- | ------ | ------------------------- |
| time     | number | 事件触发时间，单位为ms。 |
| reason  | string | 终止原因，原因范围详见[reason字段说明](#reason字段说明)。 |
| foreground | boolean | 应用是否处于前台状态。true表示应用处于前台；false表示应用处于后台。 |
| app_running_unique_id | string | 应用运行时唯一关联id。<br/>**说明**：从API version 24开始支持该参数。 |
| bundle_version | string | 应用版本信息。<br/>**说明**：从API version 24开始支持该参数。 |

### reason字段说明

| 类型   | 说明                       |
| ------- | ------------------------- |
| IllegalAudioRendererBySuspend | 应用未申请合理的后台任务，但是后台有大量音频播放。 |
| IllegalAudioCapturerBySuspend | 应用未申请合理的后台任务，但是后台有录音。 |
| LowMemoryKill | 整机低内存。 |
| OomKiller | 整机内存耗尽，无法继续分配。 |
| PowerSaveClean | 整机切换到省电模式或应急模式。 |
| ResourceLeak(AshmemLeak) | 应用Ashmem内存占用超标。 |
| ResourceLeak(GpuLeak) | 应用GPU内存占用超标。 |
| ResourceLeak(GpuRsLeak) | 应用在Render Service进程内的GPU内存占用超标。 |
| ResourceLeak(IonLeak) | 应用的Ion内存占用超标。 |
| RssThresholdKiller | 应用的RSS（Resident Size Set）占用超标。 |
| SwapFull | 整机Swap空间耗尽。 |
| Normal | 应用正常退出（如用户主动退出）。 |
| CppCrash | native层程序崩溃。 |
| JsError | js层程序崩溃。 |
| AppFreeze | 应用冻屏无响应。 |
| ResourceLeak(CES) | CES注册超限。 |
| ResourceLeak(PSSSoftLeak) | 后台应用内存占用超过检测阈值两倍，其中pss内存占比最高。 |
| ResourceLeak(PSSLeak) | 后台应用内存占用超过特定阈值，其中pss内存占比最高。 |
| ResourceLeak(IONLeak) | ION泄漏。 |
| ResourceLeak(AshmemLeak) | ASHMEM泄漏。 |
| ResourceLeak(GPURSLeak) | GPU RS内存泄漏。 |
| ResourceLeak(GPULeak) | GPU泄漏。 |
| ResourceLeak(VMALeak) | VMA泄漏。 |
| ResourceLeak(FDLeak) | FD泄漏。 |
| ResourceLeak(ThreadLeak) | 线程泄漏。 |
| ResourceLeak(KernelZoneLeak) | kernel zone泄漏。 |
| AshmemKiller | ASHMEM超限。 |
| GPUKiller | GPU占用达到阈值。 |
| DmaKiller | Dma占用达到阈值。 |
| ThreadKiller | 线程超限。 |
| IOHighload | IO高负载。 |
| CPUHighload | 应用后台CPU高负载，系统自动杀死。 |
| CPUHighloadNotify | 应用后台CPU高负载，出现弹框，用户选择停止该应用。 |
| CPUHighloadUserRequest | 应用后台CPU高负载，设置界面用户选择停止该应用。 |
| KillApplication | 应用主动退出。 |
| UnKnown | 未知原因。 |
| Restart | 应用重启。 |
| UserRequest | 最近任务上划或清理。 |
| Uninstall | 应用卸载退出。 |
| Upgrade | 应用更新退出。 |
| Logout | 用户注销时，卸载应用沙箱。 |
| UninstallStorage | 卸载存储卡。 |
| HighTemperature | 温度超限。 |
| TransientTaskTimeout | 短时任务超时6s并且处于后台。 |
| FdRs | fd个数超限。 |
