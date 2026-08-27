# @ohos.distributedMissionManager

分布式任务管理模块提供跨设备任务管理能力，包括注册和取消任务状态监听、开始和停止同步远端设备任务列表、通过任务ID和包名进行迁移任务等。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

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
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | 通过指定任务ID（missionId）的方式进行迁移任务。使用callback异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | 通过指定任务ID（missionId）的方式进行迁移任务。使用promise异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | 通过指定包名（bundleName）的方式进行迁移任务。使用callback异步回调。 |
| [continueMission](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) | 通过指定包名（bundleName）的方式进行迁移任务。使用Promise异步回调。 |
| off | 取消当前任务流转的状态监听。此接口需与on('continueStateChange')成对使用，在不需要监听时应及时调用以释放资源。 |
| on | 注册当前任务流转状态的监听。此接口需与off('continueStateChange')成对使用，不再监听时应及时取消；调用顺序为先通过on注册监听，不需要时再调用off取消监听。 |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) | 注册任务状态监听。使用callback异步回调。调用成功后，系统将开始监听指定设备上的任务状态变化，该监听需与unRegisterMissionListener成对使用，注册后应在不需要监听任务状态时及时取消。 |
| [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) | 注册任务状态监听。使用promise异步回调。调用成功后，系统将开始监听指定设备上的任务状态变化，该监听需与unRegisterMissionListener成对使用，注册后应在不需要监听任务状态时及时取消。 |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md) | 开始同步远端设备的任务列表。使用callback异步回调。使用时须与stopSyncRemoteMissions严格配对，按"先启动、后停止"的顺序执行，同步完成后应立即停止以释放系统资源。 |
| [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md) | 开始同步远端设备的任务列表。使用promise异步回调。使用时须与stopSyncRemoteMissions严格配对，按"先启动、后停止"的顺序执行，同步完成后应立即停止以释放系统资源。设备行为差异：该接口在不支持分布式业务的Wearable设备不生效。 |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md) | 停止同步远端设备的任务列表。使用callback异步回调。调用成功后，系统将停止同步指定远端设备的任务列表。需先调用startSyncRemoteMissions启动同步后再调用，未启动同步时调用不生效。 |
| [stopSyncRemoteMissions](arkts-ability-distributedmissionmanager-stopsyncremotemissions-f-sys.md) | 停止同步远端设备的任务列表。使用promise异步回调。调用成功后，系统将停止同步指定远端设备的任务列表。需先调用startSyncRemoteMissions启动同步后再调用，未启动同步时调用不生效。 |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md) | 取消任务状态监听。使用callback异步回调。停止监听前，请确保已通过registerMissionListener完成注册，否则调用无效。成功调用后，系统将不再监听该设备上的任务状态变化。 |
| [unRegisterMissionListener](arkts-ability-distributedmissionmanager-unregistermissionlistener-f-sys.md) | 取消任务状态监听。使用promise异步回调。停止监听前，请确保已通过registerMissionListener完成注册，否则调用无效。成功调用后，系统将不再监听该设备上的任务状态变化。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinueCallbackInfo](arkts-ability-distributedmissionmanager-continuecallbackinfo-i-sys.md) | 任务流转状态监听回调时返回的信息对象，包含state（流转状态）和info（流转详细信息）两个字段。state为ACTIVE表示流转处于激活状态，INACTIVE表示流转处于未激活状态。模型约束：此接口仅可在Stage模型下使用。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinueState](arkts-ability-distributedmissionmanager-continuestate-e-sys.md) | 当前任务流转状态的枚举。模型约束：此接口仅可在Stage模型下使用。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ContinuableInfo](arkts-ability-distributedmissionmanager-continuableinfo-t-sys.md) | 应用任务对应的可迁移信息。 |
| [ContinueCallback](arkts-ability-distributedmissionmanager-continuecallback-t-sys.md) | 表示跨设备迁移Mission完成后，返回迁移结果的回调函数，迁移Mission详见： [continueMission接口](arkts-ability-distributedmissionmanager-continuemission-f-sys.md) |
| [ContinueDeviceInfo](arkts-ability-distributedmissionmanager-continuedeviceinfo-t-sys.md) | 迁移任务所需的参数。 |
| [ContinueMissionInfo](arkts-ability-distributedmissionmanager-continuemissioninfo-t-sys.md) | 迁移任务所需的参数。 |
| [MissionCallback](arkts-ability-distributedmissionmanager-missioncallback-t-sys.md) | 作为可以 [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) 的入参，用于监听任务状态变化的回调函数，包含任务列表变化通知、任务快照通知和断开连接通知等功能。表示注册监听后建立的回调函数。 |
| [MissionDeviceInfo](arkts-ability-distributedmissionmanager-missiondeviceinfo-t-sys.md) | 可以作为 [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) 的入参，表示注册监听时所需参数的对象，包含deviceId等设备标识符字段。 |
| [MissionParameter](arkts-ability-distributedmissionmanager-missionparameter-t-sys.md) | 作为 [startSyncRemoteMissions](arkts-ability-distributedmissionmanager-startsyncremotemissions-f-sys.md) 的入参，表示同步远端设备任务列表时所需的参数对象，包含deviceId、fixConflict和tag等字段。 |
<!--DelEnd-->
