# @ohos.app.ability.appManager

appManager模块提供App管理的能力，包括查询当前是否处于稳定性测试场景、查询是否为ram受限设备、获取应用程序的内存大小、获取有关运行进程的信息等。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAppMemorySize](arkts-ability-getappmemorysize-f.md#getappmemorysize-1) | 获取当前应用程序可以使用的最大内存（RAM）值。使用Promise异步回调。 |
| [getAppMemorySize](arkts-ability-getappmemorysize-f.md#getappmemorysize-2) | 获取当前应用程序可以使用的最大内存（RAM）值。使用callback异步回调。 |
| [getRunningProcessInformation](arkts-ability-getrunningprocessinformation-f.md#getrunningprocessinformation-1) | 获取当前应用运行进程的相关信息。使用Promise异步回调。 |
| [getRunningProcessInformation](arkts-ability-getrunningprocessinformation-f.md#getrunningprocessinformation-2) | 获取当前应用运行进程的相关信息。使用callback异步回调。 |
| [isAppRunning](arkts-ability-isapprunning-f.md#isapprunning-1) | 判断所有用户下指定包名和分身应用索引的应用是否正在运行。使用Promise异步回调。 |
| [isRamConstrainedDevice](arkts-ability-isramconstraineddevice-f.md#isramconstraineddevice-1) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用Promise异步回调。 |
| [isRamConstrainedDevice](arkts-ability-isramconstraineddevice-f.md#isramconstraineddevice-2) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用callback异步回调。 |
| [isRunningInStabilityTest](arkts-ability-isrunninginstabilitytest-f.md#isrunninginstabilitytest-1) | 查询当前系统是否处于稳定性测试场景。使用callback异步回调。 |
| [isRunningInStabilityTest](arkts-ability-isrunninginstabilitytest-f.md#isrunninginstabilitytest-2) | 查询当前系统是否处于稳定性测试场景。使用Promise异步回调。 |
| [killProcessesByBundleName](arkts-ability-killprocessesbybundlename-f.md#killprocessesbybundlename-2) | 终止指定应用包名的应用进程。使用Promise异步回调。 |
| [off](arkts-ability-off-f.md#off-1) | 注销应用状态监听器。使用callback异步回调。 |
| [off](arkts-ability-off-f.md#off-2) | 注销应用状态监听器。使用Promise异步回调。 |
| [on](arkts-ability-on-f.md#on-1) | 注册所有应用程序的状态监听器。 |
| [on](arkts-ability-on-f.md#on-2) | 注册指定应用程序的状态监听器。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearUpAppData](arkts-ability-clearupappdata-f-sys.md#clearupappdata-1) | 根据Bundle名称和应用分身索引，清除指定应用的数据。使用Promise异步回调。 |
| [clearUpApplicationData](arkts-ability-clearupapplicationdata-f-sys.md#clearupapplicationdata-1) | 通过Bundle名称清除应用数据。使用Promise异步回调。 |
| [clearUpApplicationData](arkts-ability-clearupapplicationdata-f-sys.md#clearupapplicationdata-2) | 通过Bundle名称清除应用数据。使用callback异步回调。 |
| [getForegroundApplications](arkts-ability-getforegroundapplications-f-sys.md#getforegroundapplications-1) | 获取当前所有前台应用的信息。该应用信息由[AppStateData](arkts-ability-appstatedata-c.md)定义。使用callback异步回调。 |
| [getForegroundApplications](arkts-ability-getforegroundapplications-f-sys.md#getforegroundapplications-2) | 获取当前所有前台应用的信息。该应用信息由[AppStateData](arkts-ability-appstatedata-c.md)定义。使用Promise异步回调。 |
| [getKeepAliveAppServiceExtensions](arkts-ability-getkeepaliveappserviceextensions-f-sys.md#getkeepaliveappserviceextensions-1) | 获取所有保活的AppServiceExtensionAbility应用信息，此信息由[KeepAliveBundleInfo](arkts-ability-keepalivebundleinfo-i-sys.md)定义。使用Promise异步回调。该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |
| [getKeepAliveBundles](arkts-ability-getkeepalivebundles-f-sys.md#getkeepalivebundles-1) | 获取指定用户下指定类型的保活应用信息。该应用信息由[KeepAliveBundleInfo](arkts-ability-keepalivebundleinfo-i-sys.md)定义。使用Promise异步回调。该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。**需要权限**：ohos.permission.MANAGE_APP_KEEP_ALIVE |
| [getProcessMemoryByPid](arkts-ability-getprocessmemorybypid-f-sys.md#getprocessmemorybypid-1) | 通过pid查询对应进程占用的内存大小。使用Promise异步回调。 |
| [getProcessMemoryByPid](arkts-ability-getprocessmemorybypid-f-sys.md#getprocessmemorybypid-2) | 通过pid查询对应进程占用的内存大小。使用callback异步回调。 |
| [getRunningMultiAppInfo](arkts-ability-getrunningmultiappinfo-f-sys.md#getrunningmultiappinfo-1) | 根据应用包名获取系统中运行态的应用多开（即在一个设备上运行多个相同的应用）的相关信息。使用Promise异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-1) | 通过bundleName获取有关运行进程的信息。使用callback异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-2) | 通过bundleName和userId获取有关运行进程的信息。使用callback异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-3) | 通过bundleName获取有关运行进程的信息。使用Promise异步回调。 |
| [getRunningProcessInfoByBundleName](arkts-ability-getrunningprocessinfobybundlename-f-sys.md#getrunningprocessinfobybundlename-4) | 通过bundleName和userId获取有关运行进程的信息。使用Promise异步回调。 |
| [getRunningProcessInformationByBundleType](arkts-ability-getrunningprocessinformationbybundletype-f-sys.md#getrunningprocessinformationbybundletype-1) | 根据包类型获取当前运行进程的有关信息。使用Promise异步回调。 |
| [getSupportedProcessCachePids](arkts-ability-getsupportedprocesscachepids-f-sys.md#getsupportedprocesscachepids-1) | 查询当前应用中支持缓存后快速启动的进程PID。使用Promise异步回调。 |
| [isApplicationRunning](arkts-ability-isapplicationrunning-f-sys.md#isapplicationrunning-1) | 查询所有用户下指定包名的应用是否正在运行。使用Promise异步回调。 |
| [isApplicationRunning](arkts-ability-isapplicationrunning-f-sys.md#isapplicationrunning-2) | 查询所有用户下指定包名的应用是否正在运行。使用callback异步回调。 |
| [isSharedBundleRunning](arkts-ability-issharedbundlerunning-f-sys.md#issharedbundlerunning-1) | 检查共享库是否正在使用。使用Promise异步回调。 |
| [isSharedBundleRunning](arkts-ability-issharedbundlerunning-f-sys.md#issharedbundlerunning-2) | 检查共享库是否正在使用。使用callback异步回调。 |
| [killProcessWithAccount](arkts-ability-killprocesswithaccount-f-sys.md#killprocesswithaccount-1) | 终止account进程。使用Promise异步回调。 |
| [killProcessWithAccount](arkts-ability-killprocesswithaccount-f-sys.md#killprocesswithaccount-2) | 终止account进程。使用Promise异步回调。 |
| [killProcessWithAccount](arkts-ability-killprocesswithaccount-f-sys.md#killprocesswithaccount-3) | 终止account进程。使用callback异步回调。 |
| [killProcessesByBundleName](arkts-ability-killprocessesbybundlename-f-sys.md#killprocessesbybundlename-1) | 通过Bundle名称终止进程。使用Promise异步回调。 |
| [killProcessesByBundleName](arkts-ability-killprocessesbybundlename-f-sys.md#killprocessesbybundlename-3) | 通过Bundle名称终止进程。使用callback异步回调。 |
| [killProcessesInBatch](arkts-ability-killprocessesinbatch-f-sys.md#killprocessesinbatch-1) | 批量终止进程。使用Promise异步回调。该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。**需要权限**：ohos.permission.KILL_APP_PROCESSES |
| [off](arkts-ability-off-f-sys.md#off-3) | 注销应用启动和退出的监听器。 |
| [off](arkts-ability-off-f-sys.md#off-4) | 取消注册监听Ability首帧绘制完成事件观察者对象。 |
| [on](arkts-ability-on-f-sys.md#on-3) | 注册应用程序的状态监听器，并通过设置过滤条件来筛选所需监听的应用生命周期变化事件。 |
| [on](arkts-ability-on-f-sys.md#on-4) | 注册应用启动和退出的监听器，可用于系统应用监听所有应用的启动和退出。 |
| [on](arkts-ability-on-f-sys.md#on-5) | 注册监听Ability首帧绘制完成事件观察者对象，可用于系统应用监听Ability首帧绘制事件。 |
| [preloadApplication](arkts-ability-preloadapplication-f-sys.md#preloadapplication-1) | 预加载应用进程。接口返回成功并不代表预加载成功，具体结果以目标应用进程是否创建成功为准。使用Promise异步回调。 |
| [setKeepAliveForAppServiceExtension](arkts-ability-setkeepaliveforappserviceextension-f-sys.md#setkeepaliveforappserviceextension-1) | 为AppServiceExtensionAbility设置保活或取消保活。使用Promise异步回调。该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。 |
| [setKeepAliveForBundle](arkts-ability-setkeepaliveforbundle-f-sys.md#setkeepaliveforbundle-1) | 为指定用户下的应用设置或取消保活。使用Promise异步回调。从API version 18开始，该接口仅在2in1和Wearable设备上生效。对于API version 18之前版本，该接口仅在2in1设备上生效。其他情况下调用该接口将返回错误码801。 |
| [terminateMission](arkts-ability-terminatemission-f-sys.md#terminatemission-1) | 关闭指定的任务。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppStateFilter](arkts-ability-appstatefilter-i-sys.md) | 应用生命周期变化事件的过滤器，可作为[on](arkts-ability-on-f-sys.md#on-3)的参数用于筛选所需监听的应用生命周期变化事件。 |
| [KeepAliveBundleInfo](arkts-ability-keepalivebundleinfo-i-sys.md) | 定义应用保活信息，可以通过[getKeepAliveBundles](arkts-ability-getkeepalivebundles-f-sys.md#getkeepalivebundles-1)或[getKeepAliveAppServiceExtensions](arkts-ability-getkeepaliveappserviceextensions-f-sys.md#getkeepaliveappserviceextensions-1)获取。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ProcessState](arkts-ability-processstate-e.md) | 表示进程状态的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ApplicationState](arkts-ability-applicationstate-e-sys.md) | 应用状态，该类型为枚举，可配合[AbilityStateData](arkts-ability-abilitystatedata-c.md)返回相应的应用状态。 |
| [FilterAbilityStateType](arkts-ability-filterabilitystatetype-e-sys.md) | 表示要监听的Ability状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appstatefilter-i-sys.md)过滤想要监听的Ability状态。 |
| [FilterAppStateType](arkts-ability-filterappstatetype-e-sys.md) | 表示要监听的应用状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appstatefilter-i-sys.md)过滤想要监听的应用状态。 |
| [FilterBundleType](arkts-ability-filterbundletype-e-sys.md) | 表示要监听的的应用类型，该类型为枚举。可配合[AppStateFilter](arkts-ability-appstatefilter-i-sys.md)过滤想要监听的应用类型。 |
| [FilterCallback](arkts-ability-filtercallback-e-sys.md) | 表示要监听的回调函数，该类型为枚举。可配合[AppStateFilter](arkts-ability-appstatefilter-i-sys.md)过滤想要监听的回调函数。 |
| [FilterProcessStateType](arkts-ability-filterprocessstatetype-e-sys.md) | 表示要监听的进程状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appstatefilter-i-sys.md)过滤想要监听的进程状态。 |
| [KeepAliveAppType](arkts-ability-keepaliveapptype-e-sys.md) | 表示被保活应用的应用类型。 |
| [KeepAliveSetter](arkts-ability-keepalivesetter-e-sys.md) | 表示应用保活的设置方类型。 |
| [PreloadMode](arkts-ability-preloadmode-e-sys.md) | 表示预加载应用进程模式的枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityStateData](arkts-ability-abilitystatedata-t.md) | Ability状态信息。 |
| [AppStateData](arkts-ability-appstatedata-t.md) | 应用状态信息。 |
| [ApplicationStateObserver](arkts-ability-applicationstateobserver-t.md) | 应用状态监听器。 |
| [ProcessData](arkts-ability-processdata-t.md) | 进程数据。 |
| [ProcessInformation](arkts-ability-processinformation-t.md) | 进程信息。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbilityFirstFrameStateData](arkts-ability-abilityfirstframestatedata-t-sys.md) | UIAbility首帧绘制完成回调上报数据结构。 |
| [AbilityFirstFrameStateObserver](arkts-ability-abilityfirstframestateobserver-t-sys.md) | UIAbility首帧绘制完成事件监听对象。 |
| [AppForegroundStateObserver](arkts-ability-appforegroundstateobserver-t-sys.md) | 应用启动和退出的状态监听。 |
| [RunningMultiAppInfo](arkts-ability-runningmultiappinfo-t-sys.md) | 应用多开在运行态的结构信息。 |
<!--DelEnd-->

