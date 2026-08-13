# @ohos.application.missionManager

missionManager模块提供系统任务管理能力，包括对系统任务执行锁定、解锁、清理、切换到前台等操作。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [missionManager/missionManager](arkts-app-ability-missionmanager.md#@ohos.app.ability.missionManager)

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-unnamed-declare namespace missionManager--><!--Device-unnamed-declare namespace missionManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-depr-f-sys.md#clearAllMissions) | 清理所有未锁定的任务。使用callback异步回调。 |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-depr-f-sys.md#clearAllMissions) | 清理所有未锁定的任务。使用Promise异步回调。 |
| [clearMission](arkts-ability-missionmanager-clearmission-depr-f-sys.md#clearMission) | 清理指定任务id的任务，无论该任务是否被锁定。使用callback异步回调。 |
| [clearMission](arkts-ability-missionmanager-clearmission-depr-f-sys.md#clearMission) | 清理指定任务id的任务，无论该任务是否被锁定。使用Promise异步回调。 |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-depr-f-sys.md#getMissionInfo) | 获取单个任务信息。使用callback异步回调。 |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-depr-f-sys.md#getMissionInfo) | 获取单个任务信息。使用Promise异步回调。 |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-depr-f-sys.md#getMissionInfos) | 获取所有任务信息。使用callback异步回调。 |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-depr-f-sys.md#getMissionInfos) | 获取所有任务信息。使用Promise异步回调。 |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-depr-f-sys.md#getMissionSnapShot) | 获取任务快照。使用callback异步回调。 |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-depr-f-sys.md#getMissionSnapShot) | 获取任务快照。使用Promise异步回调。 |
| [lockMission](arkts-ability-missionmanager-lockmission-depr-f-sys.md#lockMission) | 锁定指定任务id的任务。使用callback异步回调。 |
| [lockMission](arkts-ability-missionmanager-lockmission-depr-f-sys.md#lockMission) | 锁定指定任务id的任务。使用Promise异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-depr-f-sys.md#moveMissionToFront) | 把指定任务id的任务切到前台。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-depr-f-sys.md#moveMissionToFront) | 把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-depr-f-sys.md#moveMissionToFront) | 把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。 |
| [registerMissionListener](arkts-ability-missionmanager-registermissionlistener-depr-f-sys.md#registerMissionListener) | 注册系统任务状态监听器。 |
| [unlockMission](arkts-ability-missionmanager-unlockmission-depr-f-sys.md#unlockMission) | 解锁指定任务id的任务。使用callback异步回调。 |
| [unlockMission](arkts-ability-missionmanager-unlockmission-depr-f-sys.md#unlockMission) | 解锁指定任务id的任务。使用Promise异步回调。 |
| [unregisterMissionListener](arkts-ability-missionmanager-unregistermissionlistener-depr-f-sys.md#unregisterMissionListener) | 解注册任务状态监听器。使用callback异步回调。 |
| [unregisterMissionListener](arkts-ability-missionmanager-unregistermissionlistener-depr-f-sys.md#unregisterMissionListener) | 解注册任务状态监听器。使用Promise异步回调。 |
<!--DelEnd-->

