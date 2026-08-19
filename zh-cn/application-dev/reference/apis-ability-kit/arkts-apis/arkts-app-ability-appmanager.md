# @ohos.app.ability.appManager

appManager模块提供App管理的能力，包括查询当前是否处于稳定性测试场景、查询是否为ram受限设备、获取应用程序的内存大小、获取有关运行进程的信息等。

**起始版本：** 23

<!--Device-unnamed-declare namespace appManager--><!--Device-unnamed-declare namespace appManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-f.md) | 获取当前应用程序可以使用的最大内存（RAM）值。使用Promise异步回调。 |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-f.md) | 获取当前应用程序可以使用的最大内存（RAM）值。使用callback异步回调。 |
| [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md) | 获取当前应用运行进程的相关信息。使用Promise异步回调。 |
| [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md) | 获取当前应用运行进程的相关信息。使用callback异步回调。 |
| [isAppRunning](arkts-ability-appmanager-isapprunning-f.md) | 判断所有用户下指定包名和分身应用索引的应用是否正在运行。使用Promise异步回调。 |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-f.md) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用Promise异步回调。 |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-f.md) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用callback异步回调。 |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-f.md) | 查询当前系统是否处于稳定性测试场景。使用callback异步回调。 |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-f.md) | 查询当前系统是否处于稳定性测试场景。使用Promise异步回调。 |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f.md) | 终止指定应用包名的应用进程。使用Promise异步回调。 |
| [offApplicationStateChange](arkts-ability-appmanager-offapplicationstatechange-f.md) | 注销应用状态监听器。使用callback异步回调。 |
| [offApplicationStateChange](arkts-ability-appmanager-offapplicationstatechange-f.md) | 注销应用状态监听器。使用Promise异步回调。 |
| [off_applicationState](arkts-ability-appmanager-offapplicationstate-f.md#offapplicationstate) | 注销应用状态监听器。使用callback异步回调。 |
| [off_applicationState](arkts-ability-appmanager-offapplicationstate-f.md#offapplicationstate) | 注销应用状态监听器。使用Promise异步回调。 |
| [onApplicationStateChange](arkts-ability-appmanager-onapplicationstatechange-f.md) | 注册所有应用程序的状态监听器。 |
| [onApplicationStateChange](arkts-ability-appmanager-onapplicationstatechange-f.md) | 注册指定应用程序的状态监听器。 |
| [on_applicationState](arkts-ability-appmanager-onapplicationstate-f.md#onapplicationstate) | 注册所有应用程序的状态监听器。 |
| [on_applicationState](arkts-ability-appmanager-onapplicationstate-f.md#onapplicationstate) | 注册指定应用程序的状态监听器。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearUpAppData](arkts-ability-appmanager-clearupappdata-f-sys.md) | 根据Bundle名称和应用分身索引，清除指定应用的数据。使用Promise异步回调。 |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-f-sys.md) | 通过Bundle名称清除应用数据。使用Promise异步回调。 |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-f-sys.md) | 通过Bundle名称清除应用数据。使用callback异步回调。 |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-f-sys.md) | 获取当前所有前台应用的信息。该应用信息由[AppStateData](arkts-ability-appstatedata-c.md)定义。使用callback异步回调。 |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-f-sys.md) | 获取当前所有前台应用的信息。该应用信息由[AppStateData](arkts-ability-appstatedata-c.md)定义。使用Promise异步回调。 |
| [getKeepAliveAppServiceExtensions](arkts-ability-appmanager-getkeepaliveappserviceextensions-f-sys.md) | 获取所有保活的AppServiceExtensionAbility应用信息，此信息由[KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md)定义。使用Promise异步 回调。 该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |
| [getKeepAliveBundles](arkts-ability-appmanager-getkeepalivebundles-f-sys.md) | 获取指定用户下指定类型的保活应用信息。该应用信息由[KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md)定义。使用Promise异步回调。 该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。 **需要权限**：ohos.permission.MANAGE_APP_KEEP_ALIVE |
| [getProcessMemoryByPid](arkts-ability-appmanager-getprocessmemorybypid-f-sys.md) | 通过pid查询对应进程占用的内存大小。使用Promise异步回调。 |
| [getProcessMemoryByPid](arkts-ability-appmanager-getprocessmemorybypid-f-sys.md) | 通过pid查询对应进程占用的内存大小。使用callback异步回调。 |
| [getRunningMultiAppInfo](arkts-ability-appmanager-getrunningmultiappinfo-f-sys.md) | 根据应用包名获取系统中运行态的应用多开（即在一个设备上运行多个相同的应用）的相关信息。使用Promise异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md) | 通过bundleName获取有关运行进程的信息。使用callback异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md) | 通过bundleName和userId获取有关运行进程的信息。使用callback异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md) | 通过bundleName获取有关运行进程的信息。使用Promise异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md) | 通过bundleName和userId获取有关运行进程的信息。使用Promise异步回调。 |
| [getRunningProcessInformationByBundleType](arkts-ability-appmanager-getrunningprocessinformationbybundletype-f-sys.md) | 根据包类型获取当前运行进程的有关信息。使用Promise异步回调。 |
| [getSupportedProcessCachePids](arkts-ability-appmanager-getsupportedprocesscachepids-f-sys.md) | 查询当前应用中支持缓存后快速启动的进程PID。使用Promise异步回调。 |
| [isApplicationRunning](arkts-ability-appmanager-isapplicationrunning-f-sys.md) | 查询所有用户下指定包名的应用是否正在运行。使用Promise异步回调。 |
| [isApplicationRunning](arkts-ability-appmanager-isapplicationrunning-f-sys.md) | 查询所有用户下指定包名的应用是否正在运行。使用callback异步回调。 |
| [isSharedBundleRunning](arkts-ability-appmanager-issharedbundlerunning-f-sys.md) | 检查共享库是否正在使用。使用Promise异步回调。 |
| [isSharedBundleRunning](arkts-ability-appmanager-issharedbundlerunning-f-sys.md) | 检查共享库是否正在使用。使用callback异步回调。 |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md) | 终止account进程。使用Promise异步回调。 |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md) | 终止account进程。使用Promise异步回调。 |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md) | 终止account进程。使用callback异步回调。 |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f-sys.md) | 通过Bundle名称终止进程。使用Promise异步回调。 |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f-sys.md) | 通过Bundle名称终止进程。使用callback异步回调。 |
| [killProcessesInBatch](arkts-ability-appmanager-killprocessesinbatch-f-sys.md) | 批量终止进程。使用Promise异步回调。 该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。 **需要权限**：ohos.permission.KILL_APP_PROCESSES |
| [offAbilityFirstFrameStateChange](arkts-ability-appmanager-offabilityfirstframestatechange-f-sys.md) | 取消注册监听Ability首帧绘制完成事件观察者对象。 |
| [offAppForegroundStateChange](arkts-ability-appmanager-offappforegroundstatechange-f-sys.md) | 注销应用启动和退出的监听器。 |
| [off_abilityFirstFrameState](arkts-ability-appmanager-offabilityfirstframestate-f-sys.md#offabilityfirstframestate) | 取消注册监听Ability首帧绘制完成事件观察者对象。 |
| [off_appForegroundState](arkts-ability-appmanager-offappforegroundstate-f-sys.md#offappforegroundstate) | 注销应用启动和退出的监听器。 |
| [onAbilityFirstFrameStateChange](arkts-ability-appmanager-onabilityfirstframestatechange-f-sys.md) | 注册监听Ability首帧绘制完成事件观察者对象，可用于系统应用监听Ability首帧绘制事件。 |
| [onAppForegroundStateChange](arkts-ability-appmanager-onappforegroundstatechange-f-sys.md) | 注册应用启动和退出的监听器，可用于系统应用监听所有应用的启动和退出。 |
| [onApplicationStateChange](arkts-ability-appmanager-onapplicationstatechange-f-sys.md) | 注册应用程序的状态监听器，并通过设置过滤条件来筛选所需监听的应用生命周期变化事件。 |
| [on_abilityFirstFrameState](arkts-ability-appmanager-onabilityfirstframestate-f-sys.md#onabilityfirstframestate) | 注册监听Ability首帧绘制完成事件观察者对象，可用于系统应用监听Ability首帧绘制事件。 |
| [on_appForegroundState](arkts-ability-appmanager-onappforegroundstate-f-sys.md#onappforegroundstate) | 注册应用启动和退出的监听器，可用于系统应用监听所有应用的启动和退出。 |
| [on_applicationState](arkts-ability-appmanager-onapplicationstate-f-sys.md#onapplicationstate) | 注册应用程序的状态监听器，并通过设置过滤条件来筛选所需监听的应用生命周期变化事件。 |
| [preloadApplication](arkts-ability-appmanager-preloadapplication-f-sys.md) | 预加载应用进程。接口返回成功并不代表预加载成功，具体结果以目标应用进程是否创建成功为准。使用Promise异步回调。 |
| [setKeepAliveForAppServiceExtension](arkts-ability-appmanager-setkeepaliveforappserviceextension-f-sys.md) | 为AppServiceExtensionAbility设置保活或取消保活。使用Promise异步回调。 该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |
| [setKeepAliveForBundle](arkts-ability-appmanager-setkeepaliveforbundle-f-sys.md) | 为指定用户下的应用设置或取消保活。使用Promise异步回调。 从API version 18开始，该接口仅在2in1和Wearable设备上生效。对于API version 18之前版本，该接口仅在2in1设备上生效。其他情况下调用该接口将返回错误码801。 |
| [terminateMission](arkts-ability-appmanager-terminatemission-f-sys.md) | 关闭指定的任务。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) | 应用生命周期变化事件的过滤器，可作为 [on](arkts-ability-appmanager-onapplicationstate-f.md#onapplicationstate)的参数用 于筛选所需监听的应用生命周期变化事件。 |
| [KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md) | 定义应用保活信息，可以通过[getKeepAliveBundles](arkts-ability-appmanager-getkeepalivebundles-f-sys.md)或 [getKeepAliveAppServiceExtensions](arkts-ability-appmanager-getkeepaliveappserviceextensions-f-sys.md)获取。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ProcessState](arkts-ability-appmanager-processstate-e.md) | 表示进程状态的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ApplicationState](arkts-ability-appmanager-applicationstate-e-sys.md) | 应用状态，该类型为枚举，可配合[AbilityStateData](arkts-ability-abilitystatedata-c.md)返回相应的应用状态。 |
| [FilterAbilityStateType](arkts-ability-appmanager-filterabilitystatetype-e-sys.md) | 表示要监听的Ability状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的Ability状态。 |
| [FilterAppStateType](arkts-ability-appmanager-filterappstatetype-e-sys.md) | 表示要监听的应用状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的应用状态。 |
| [FilterBundleType](arkts-ability-appmanager-filterbundletype-e-sys.md) | 表示要监听的的应用类型，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的应用类型。 |
| [FilterCallback](arkts-ability-appmanager-filtercallback-e-sys.md) | 表示要监听的回调函数，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的回调函数。 |
| [FilterProcessStateType](arkts-ability-appmanager-filterprocessstatetype-e-sys.md) | 表示要监听的进程状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的进程状态。 |
| [KeepAliveAppType](arkts-ability-appmanager-keepaliveapptype-e-sys.md) | 表示被保活应用的应用类型。 |
| [KeepAliveSetter](arkts-ability-appmanager-keepalivesetter-e-sys.md) | 表示应用保活的设置方类型。 |
| [PreloadMode](arkts-ability-appmanager-preloadmode-e-sys.md) | 表示预加载应用进程模式的枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityStateData](arkts-ability-appmanager-abilitystatedata-t.md) | Ability状态信息。 |
| [AppStateData](arkts-ability-appmanager-appstatedata-t.md) | 应用状态信息。 |
| [ApplicationStateObserver](arkts-ability-appmanager-applicationstateobserver-t.md) | 应用状态监听器。 |
| [ProcessData](arkts-ability-appmanager-processdata-t.md) | 进程数据。 |
| [ProcessInformation](arkts-ability-appmanager-processinformation-t.md) | 进程信息。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbilityFirstFrameStateData](arkts-ability-appmanager-abilityfirstframestatedata-t-sys.md) | UIAbility首帧绘制完成回调上报数据结构。 |
| [AbilityFirstFrameStateObserver](arkts-ability-appmanager-abilityfirstframestateobserver-t-sys.md) | UIAbility首帧绘制完成事件监听对象。 |
| [AppForegroundStateObserver](arkts-ability-appmanager-appforegroundstateobserver-t-sys.md) | 应用启动和退出的状态监听。 |
| [RunningMultiAppInfo](arkts-ability-appmanager-runningmultiappinfo-t-sys.md) | 应用多开在运行态的结构信息。 |
<!--DelEnd-->

