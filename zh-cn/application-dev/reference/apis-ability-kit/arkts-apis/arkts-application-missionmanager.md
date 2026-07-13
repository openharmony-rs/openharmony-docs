# @ohos.application.missionManager

missionManager模块提供系统任务管理能力，包括对系统任务执行锁定、解锁、清理、切换到前台等操作。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** missionManager/missionManager

**需要权限：** ohos.permission.MANAGE_MISSIONS

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearAllMissions](arkts-ability-clearallmissions-depr-f-sys.md#clearallmissions-1) | 清理所有未锁定的任务。使用callback异步回调。 |
| [clearAllMissions](arkts-ability-clearallmissions-depr-f-sys.md#clearallmissions-2) | 清理所有未锁定的任务。使用Promise异步回调。 |
| [clearMission](arkts-ability-clearmission-depr-f-sys.md#clearmission-1) | 清理指定任务id的任务，无论该任务是否被锁定。使用callback异步回调。 |
| [clearMission](arkts-ability-clearmission-depr-f-sys.md#clearmission-2) | 清理指定任务id的任务，无论该任务是否被锁定。使用Promise异步回调。 |
| [getMissionInfo](arkts-ability-getmissioninfo-depr-f-sys.md#getmissioninfo-1) | 获取单个任务信息。使用callback异步回调。 |
| [getMissionInfo](arkts-ability-getmissioninfo-depr-f-sys.md#getmissioninfo-2) | 获取单个任务信息。使用Promise异步回调。 |
| [getMissionInfos](arkts-ability-getmissioninfos-depr-f-sys.md#getmissioninfos-1) | 获取所有任务信息。使用callback异步回调。 |
| [getMissionInfos](arkts-ability-getmissioninfos-depr-f-sys.md#getmissioninfos-2) | 获取所有任务信息。使用Promise异步回调。 |
| [getMissionSnapShot](arkts-ability-getmissionsnapshot-depr-f-sys.md#getmissionsnapshot-1) | 获取任务快照。使用callback异步回调。 |
| [getMissionSnapShot](arkts-ability-getmissionsnapshot-depr-f-sys.md#getmissionsnapshot-2) | 获取任务快照。使用Promise异步回调。 |
| [lockMission](arkts-ability-lockmission-depr-f-sys.md#lockmission-1) | 锁定指定任务id的任务。使用callback异步回调。 |
| [lockMission](arkts-ability-lockmission-depr-f-sys.md#lockmission-2) | 锁定指定任务id的任务。使用Promise异步回调。 |
| [moveMissionToFront](arkts-ability-movemissiontofront-depr-f-sys.md#movemissiontofront-1) | 把指定任务id的任务切到前台。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-movemissiontofront-depr-f-sys.md#movemissiontofront-2) | 把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-movemissiontofront-depr-f-sys.md#movemissiontofront-3) | 把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。 |
| [registerMissionListener](arkts-ability-registermissionlistener-depr-f-sys.md#registermissionlistener-1) | 注册系统任务状态监听器。 |
| [unlockMission](arkts-ability-unlockmission-depr-f-sys.md#unlockmission-1) | 解锁指定任务id的任务。使用callback异步回调。 |
| [unlockMission](arkts-ability-unlockmission-depr-f-sys.md#unlockmission-2) | 解锁指定任务id的任务。使用Promise异步回调。 |
| [unregisterMissionListener](arkts-ability-unregistermissionlistener-depr-f-sys.md#unregistermissionlistener-1) | 解注册任务状态监听器。使用callback异步回调。 |
| [unregisterMissionListener](arkts-ability-unregistermissionlistener-depr-f-sys.md#unregistermissionlistener-2) | 解注册任务状态监听器。使用Promise异步回调。 |
<!--DelEnd-->

