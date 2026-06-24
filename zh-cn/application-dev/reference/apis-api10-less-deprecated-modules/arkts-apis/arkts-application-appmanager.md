# @ohos.application.appManager

appManager模块提供应用管理的能力，包括查询当前系统是否处于稳定性测试场景、查询当前设备是否为RAM（Random Access Memory，随机存取存储器）受限设备、获取当前应用程序可以使用的最大内存值、获取有关运行进程的
信息等。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** appManager/appManager

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[clearUpApplicationData](arkts-api10lessdeprecatedmodules-appmanager-clearupapplicationdata-f-sys.md#clearUpApplicationData-1) | 通过Bundle名称清除应用数据。使用Promise异步回调。<br/> |
| <!--DelRow-->[clearUpApplicationData](arkts-api10lessdeprecatedmodules-appmanager-clearupapplicationdata-f-sys.md#clearUpApplicationData-2) | 通过Bundle名称清除应用数据。使用callback异步回调。<br/> |
| [getAppMemorySize](arkts-api10lessdeprecatedmodules-appmanager-getappmemorysize-f.md#getAppMemorySize-1) | 获取当前应用程序可以使用的最大内存（RAM）值。使用Promise异步回调。<br/> |
| [getAppMemorySize](arkts-api10lessdeprecatedmodules-appmanager-getappmemorysize-f.md#getAppMemorySize-2) | 获取当前应用程序可以使用的最大内存（RAM）值。使用callback异步回调。<br/> |
| <!--DelRow-->[getForegroundApplications](arkts-api10lessdeprecatedmodules-appmanager-getforegroundapplications-f-sys.md#getForegroundApplications-1) | 获取所有当前处于前台的应用信息。该应用信息由[AppStateData](application/AppStateData:AppStateData)定义。使用callback异步回调。<br/> |
| <!--DelRow-->[getForegroundApplications](arkts-api10lessdeprecatedmodules-appmanager-getforegroundapplications-f-sys.md#getForegroundApplications-2) | 获取所有当前处于前台的应用信息。该应用信息由[AppStateData](application/AppStateData:AppStateData)定义。使用Promise异步回调。<br/> |
| [getProcessRunningInfos](arkts-api10lessdeprecatedmodules-appmanager-getprocessrunninginfos-f.md#getProcessRunningInfos-1) | 获取有关运行进程的信息。使用Promise异步回调。<br/><br/>&gt; 从 API Version 9 开始废弃，建议使用<br/>&gt; [appManager.getRunningProcessInformation](../../apis-ability-kit/arkts-apis/arkts-ability-appmanager-getrunningprocessinformation-f.md#getRunningProcessInformation-1)<br/>&gt; 替代。<br/> |
| [getProcessRunningInfos](arkts-api10lessdeprecatedmodules-appmanager-getprocessrunninginfos-f.md#getProcessRunningInfos-2) | 获取有关运行进程的信息。使用callback异步回调。<br/><br/>&gt; 从 API Version 9 开始废弃，建议使用<br/>&gt; [appManager.getRunningProcessInformation](../../apis-ability-kit/arkts-apis/arkts-ability-appmanager-getrunningprocessinformation-f.md#getRunningProcessInformation-1)<br/>&gt; 替代。<br/> |
| [isRamConstrainedDevice](arkts-api10lessdeprecatedmodules-appmanager-isramconstraineddevice-f.md#isRamConstrainedDevice-1) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用Promise异步回调。<br/> |
| [isRamConstrainedDevice](arkts-api10lessdeprecatedmodules-appmanager-isramconstraineddevice-f.md#isRamConstrainedDevice-2) | 查询当前设备是否为RAM受限设备（内存资源严重受限的设备）。使用callback异步回调。<br/> |
| [isRunningInStabilityTest](arkts-api10lessdeprecatedmodules-appmanager-isrunninginstabilitytest-f.md#isRunningInStabilityTest-1) | 查询当前系统是否处于稳定性测试场景。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 稳定性测试场景指为验证应用在复杂、极端或长期运行条件下的可靠性而设计的特定测试环境。<br/> |
| [isRunningInStabilityTest](arkts-api10lessdeprecatedmodules-appmanager-isrunninginstabilitytest-f.md#isRunningInStabilityTest-2) | 查询当前系统是否处于稳定性测试场景。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 稳定性测试场景指为验证应用在复杂、极端或长期运行条件下的可靠性而设计的特定测试环境。<br/> |
| <!--DelRow-->[killProcessWithAccount](arkts-api10lessdeprecatedmodules-appmanager-killprocesswithaccount-f-sys.md#killProcessWithAccount-1) | 切断account进程。使用Promise异步回调。<br/> |
| <!--DelRow-->[killProcessWithAccount](arkts-api10lessdeprecatedmodules-appmanager-killprocesswithaccount-f-sys.md#killProcessWithAccount-2) | 切断account进程。使用callback异步回调。<br/> |
| <!--DelRow-->[killProcessesByBundleName](arkts-api10lessdeprecatedmodules-appmanager-killprocessesbybundlename-f-sys.md#killProcessesByBundleName-1) | 通过Bundle名称终止进程。使用Promise异步回调。<br/> |
| <!--DelRow-->[killProcessesByBundleName](arkts-api10lessdeprecatedmodules-appmanager-killprocessesbybundlename-f-sys.md#killProcessesByBundleName-2) | 通过Bundle名称终止进程。使用callback异步回调。<br/> |
| <!--DelRow-->[registerApplicationStateObserver](arkts-api10lessdeprecatedmodules-appmanager-registerapplicationstateobserver-f-sys.md#registerApplicationStateObserver-1) | 注册全部应用程序状态观测器。<br/> |
| <!--DelRow-->[unregisterApplicationStateObserver](arkts-api10lessdeprecatedmodules-appmanager-unregisterapplicationstateobserver-f-sys.md#unregisterApplicationStateObserver-1) | 取消注册应用程序状态观测器。使用callback异步回调。<br/> |
| <!--DelRow-->[unregisterApplicationStateObserver](arkts-api10lessdeprecatedmodules-appmanager-unregisterapplicationstateobserver-f-sys.md#unregisterApplicationStateObserver-2) | 取消注册应用程序状态观测器。使用Promise异步回调。<br/> |

