# @ohos.application.appManager

appManager模块提供应用管理的能力，包括查询当前系统是否处于稳定性测试场景、查询当前设备是否为RAM（Random Access Memory，随机存取存储器）受限设备、获取当前应用程序可以使用的最大内存值、获取有关运行进程的信息等。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** appManager/appManager

<!--Device-unnamed-declare namespace appManager--><!--Device-unnamed-declare namespace appManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-depr-f.md#getappmemorysize) | 获取当前应用程序可以使用的最大内存（RAM）值。使用Promise异步回调。 |
| [getAppMemorySize](arkts-ability-appmanager-getappmemorysize-depr-f.md#getappmemorysize-1) | 获取当前应用程序可以使用的最大内存（RAM）值。使用callback异步回调。 |
| [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md#getprocessrunninginfos) | 获取有关运行进程的信息。使用Promise异步回调。 > 从 API Version 9 开始废弃，建议使用  > [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getrunningprocessinformation)  > 替代。 |
| [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md#getprocessrunninginfos-1) | 获取有关运行进程的信息。使用callback异步回调。 > 从 API Version 9 开始废弃，建议使用  > [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getrunningprocessinformation)  > 替代。 |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-depr-f.md#isramconstraineddevice) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用Promise异步回调。 |
| [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-depr-f.md#isramconstraineddevice-1) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用callback异步回调。 |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-depr-f.md#isrunninginstabilitytest) | 查询当前系统是否处于稳定性测试场景。使用callback异步回调。 |
| [isRunningInStabilityTest](arkts-ability-appmanager-isrunninginstabilitytest-depr-f.md#isrunninginstabilitytest-1) | 查询当前系统是否处于稳定性测试场景。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-depr-f-sys.md#clearupapplicationdata) | 通过Bundle名称清除应用数据。使用Promise异步回调。 |
| [clearUpApplicationData](arkts-ability-appmanager-clearupapplicationdata-depr-f-sys.md#clearupapplicationdata-1) | 通过Bundle名称清除应用数据。使用callback异步回调。 |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-depr-f-sys.md#getforegroundapplications) | 获取所有当前处于前台的应用信息。该应用信息由[AppStateData](arkts-ability-appstatedata-c.md)定义。使用callback异步回调。 |
| [getForegroundApplications](arkts-ability-appmanager-getforegroundapplications-depr-f-sys.md#getforegroundapplications-1) | 获取所有当前处于前台的应用信息。该应用信息由[AppStateData](arkts-ability-appstatedata-c.md)定义。使用Promise异步回调。 |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-depr-f-sys.md#killprocesswithaccount) | 切断account进程。使用Promise异步回调。 |
| [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-depr-f-sys.md#killprocesswithaccount-1) | 切断account进程。使用callback异步回调。 |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-depr-f-sys.md#killprocessesbybundlename) | 通过Bundle名称终止进程。使用Promise异步回调。 |
| [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-depr-f-sys.md#killprocessesbybundlename-1) | 通过Bundle名称终止进程。使用callback异步回调。 |
| [registerApplicationStateObserver](arkts-ability-appmanager-registerapplicationstateobserver-depr-f-sys.md#registerapplicationstateobserver) | 注册全部应用程序状态观测器。 |
| [unregisterApplicationStateObserver](arkts-ability-appmanager-unregisterapplicationstateobserver-depr-f-sys.md#unregisterapplicationstateobserver) | 取消注册应用程序状态观测器。使用callback异步回调。 |
| [unregisterApplicationStateObserver](arkts-ability-appmanager-unregisterapplicationstateobserver-depr-f-sys.md#unregisterapplicationstateobserver-1) | 取消注册应用程序状态观测器。使用Promise异步回调。 |
<!--DelEnd-->

