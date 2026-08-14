# @ohos.distributedMissionManager

分布式任务管理模块提供跨设备任务管理能力，包括注册和取消任务状态监听、开始和停止同步远端设备任务列表、通过任务ID和包名进行迁移任务等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace distributedMissionManager--><!--Device-unnamed-declare namespace distributedMissionManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continueMission) | 通过指定任务ID（missionId）的方式进行迁移任务。使用callback异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continueMission（系统接口）) | 通过指定任务ID（missionId）的方式进行迁移任务。使用promise异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continueMission（系统接口）) | 通过指定包名（bundleName）的方式进行迁移任务。使用callback异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md#continueMission（系统接口）) | 通过指定包名（bundleName）的方式进行迁移任务。使用Promise异步回调。 |
| [offContinueStateChange](arkts-ability-distributedmissionmanager-offcontinuestatechange-f-sys.md#offContinueStateChange) | Continue mission |
| off_continueStateChange | 取消当前任务流转的状态监听。 |
| [onContinueStateChange](arkts-ability-distributedmissionmanager-oncontinuestatechange-f-sys.md#onContinueStateChange) | Register continuable info listener to ams. |
| on_continueStateChange | 注册当前任务流转状态的监听。 |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md#registerMissionListener) | 注册任务状态监听。使用callback异步回调。 |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md#registerMissionListener（系统接口）) | 注册任务状态监听。使用promise异步回调。 |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md#startSyncRemoteMissions) | 开始同步远端设备的任务列表。使用callback异步回调。 |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md#startSyncRemoteMissions（系统接口）) | 开始同步远端设备的任务列表。使用promise异步回调。 |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md#stopSyncRemoteMissions) | 停止同步远端设备的任务列表。使用callback异步回调。 |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md#stopSyncRemoteMissions（系统接口）) | 停止同步远端设备的任务列表。使用promise异步回调。 |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md#unRegisterMissionListener) | 取消任务状态监听。使用callback异步回调。 |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md#unRegisterMissionListener（系统接口）) | 取消任务状态监听。使用promise异步回调。 |
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
| [ContinuableInfo](arkts-ability-distributedmissionmanager-continuableinfo-t-sys.md) | 应用任务对应的可迁移信息。 |
| [ContinueCallback](arkts-ability-distributedmissionmanager-continuecallback-t-sys.md) | 注册用于通知迁移结果的回调。 |
| [ContinueDeviceInfo](arkts-ability-distributedmissionmanager-continuedeviceinfo-t-sys.md) | 迁移任务所需的参数。 |
| [ContinueMissionInfo](arkts-ability-distributedmissionmanager-continuemissioninfo-t-sys.md) | 迁移任务所需的参数。 |
| [MissionCallback](arkts-ability-distributedmissionmanager-missioncallback-t-sys.md) | 作为可以 [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md#registerMissionListener（系统接口）) 的入参，表示开始同步后，建立的回调函数。 |
| [MissionDeviceInfo](arkts-ability-distributedmissionmanager-missiondeviceinfo-t-sys.md) | 可以作为 [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md#registerMissionListener（系统接口）) 的入参，表示注册监听时所需参数的枚举。 |
| [MissionParameter](arkts-ability-distributedmissionmanager-missionparameter-t-sys.md) | 作为 [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md#startSyncRemoteMissions（系统接口）) 的入参，表示同步时所需参数的枚举。 |
<!--DelEnd-->

