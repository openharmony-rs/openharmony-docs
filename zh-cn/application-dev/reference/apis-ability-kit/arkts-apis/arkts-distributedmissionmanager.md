# @ohos.distributedMissionManager

分布式任务管理模块提供跨设备任务管理能力，包括注册和取消任务状态监听、开始和停止同步远端设备任务列表、通过任务ID和包名进行迁移任务等。

**起始版本：** 9

<!--Device-unnamed-declare namespace distributedMissionManager--><!--Device-unnamed-declare namespace distributedMissionManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission-1) | 通过指定任务ID（missionId）的方式进行迁移任务。使用callback异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission-2) | 通过指定任务ID（missionId）的方式进行迁移任务。使用promise异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission-3) | 通过指定包名（bundleName）的方式进行迁移任务。使用callback异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continuemission-4) | 通过指定包名（bundleName）的方式进行迁移任务。使用Promise异步回调。 |
| [off](arkts-ability-distributedmissionmanager-off-f-sys.md#off-1) | 取消当前任务流转的状态监听。 |
| [on](arkts-ability-distributedmissionmanager-on-f-sys.md#on-1) | 注册当前任务流转状态的监听。 |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md#registermissionlistener-1) | 注册任务状态监听。使用callback异步回调。 |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md#registermissionlistener-2) | 注册任务状态监听。使用promise异步回调。 |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md#startsyncremotemissions-1) | 开始同步远端设备的任务列表。使用callback异步回调。 |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md#startsyncremotemissions-2) | 开始同步远端设备的任务列表。使用promise异步回调。 |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md#stopsyncremotemissions-1) | 停止同步远端设备的任务列表。使用callback异步回调。 |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md#stopsyncremotemissions-2) | 停止同步远端设备的任务列表。使用promise异步回调。 |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md#unregistermissionlistener-1) | 取消任务状态监听。使用callback异步回调。 |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md#unregistermissionlistener-2) | 取消任务状态监听。使用promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md) | 当前任务流转状态监听的回调信息，包含流转状态和流转信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinueState](arkts-ability-distributedmissionmanager-continuestate-e-sys.md) | 当前任务流转状态的枚举。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinuableInfo](arkts-ability-distributedmissionmanager-continuableinfo-t-sys.md) | Continuable information corresponding to ability. |
| [ContinueCallback](arkts-ability-distributedmissionmanager-continuecallback-t-sys.md) | ContinueCallback registered for notify continue result. |
| [ContinueDeviceInfo](arkts-ability-distributedmissionmanager-continuedeviceinfo-t-sys.md) | Parameters corresponding to continue mission. |
| [ContinueMissionInfo](arkts-ability-distributedmissionmanager-continuemissioninfo-t-sys.md) | Parameters corresponding to continue mission. |
| [MissionCallback](arkts-ability-distributedmissionmanager-missioncallback-t-sys.md) | 作为可以[registerMissionListener](registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback&lt;void&gt;))的入参，表示开始同步后，建立的回调函数。 |
| [MissionDeviceInfo](arkts-ability-distributedmissionmanager-missiondeviceinfo-t-sys.md) | 可以作为[registerMissionListener](registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback&lt;void&gt;))的入参，表示注册监听时所需参数的枚举。 |
| [MissionParameter](arkts-ability-distributedmissionmanager-missionparameter-t-sys.md) | 作为[startSyncRemoteMissions](startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback&lt;void&gt;))的入参，表示同步时所需参数的枚举。 |
<!--DelEnd-->

