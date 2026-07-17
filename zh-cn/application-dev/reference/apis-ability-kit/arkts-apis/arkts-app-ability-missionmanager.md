# @ohos.app.ability.missionManager

missionManager模块提供系统任务管理能力，包括对系统任务执行锁定、解锁、清理、切换到前台等操作。

**起始版本：** 9

<!--Device-unnamed-declare namespace missionManager--><!--Device-unnamed-declare namespace missionManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md#clearallmissions-1) | 清理所有未锁定的任务。使用callback异步回调。 |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md#clearallmissions-2) | 清理所有未锁定的任务。使用Promise异步回调。 |
| [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md#clearmission-1) | 清理指定任务ID的任务，无论该任务是否被锁定。使用callback异步回调。 |
| [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md#clearmission-2) | 清理指定任务ID的任务，无论该任务是否被锁定。使用Promise异步回调。 |
| [getLowResolutionMissionSnapShot](arkts-ability-missionmanager-getlowresolutionmissionsnapshot-f-sys.md#getlowresolutionmissionsnapshot-1) | 获取任务低分辨率快照。使用callback异步回调。 |
| [getLowResolutionMissionSnapShot](arkts-ability-missionmanager-getlowresolutionmissionsnapshot-f-sys.md#getlowresolutionmissionsnapshot-2) | 获取任务低分辨率快照。使用Promise异步回调。 |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getmissioninfo-1) | 获取任务信息。使用callback异步回调。 |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getmissioninfo-2) | 获取任务信息。使用Promise异步回调。 |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getmissioninfos-1) | 获取所有任务信息。使用callback异步回调。 |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getmissioninfos-2) | 获取所有任务信息。使用Promise异步回调。 |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md#getmissionsnapshot-1) | 获取任务快照。使用callback异步回调。 |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md#getmissionsnapshot-2) | 获取任务快照。使用Promise异步回调。 |
| [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md#lockmission-1) | 锁定指定任务ID的任务。使用callback异步回调。 |
| [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md#lockmission-2) | 锁定指定任务ID的任务。使用Promise异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#movemissiontofront-1) | 把指定任务ID的任务切到前台。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#movemissiontofront-2) | 把指定任务ID的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#movemissiontofront-3) | 把指定任务ID的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。 |
| [moveMissionsToBackground](arkts-ability-missionmanager-movemissionstobackground-f-sys.md#movemissionstobackground-1) | 将指定任务批量切到后台，返回的结果任务ID按被隐藏时的任务层级排序。使用callback异步回调。 |
| [moveMissionsToBackground](arkts-ability-missionmanager-movemissionstobackground-f-sys.md#movemissionstobackground-2) | 将指定任务批量切到后台，返回的结果按被隐藏时的任务层级排序。使用Promise异步回调。 |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#movemissionstoforeground-1) | 将指定任务批量切到前台。使用callback异步回调。 |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#movemissionstoforeground-2) | 将指定任务批量切换到前台，并将任务ID等于topMission的任务移动到最顶层。使用callback异步回调。 |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#movemissionstoforeground-3) | 将指定任务批量切到前台，并将任务ID等于topMission的任务移动到最顶层。使用Promise异步回调。 |
| [off](arkts-ability-missionmanager-off-f-sys.md#off-1) | 解注册任务状态监听器。使用callback异步回调。 |
| [off](arkts-ability-missionmanager-off-f-sys.md#off-2) | 解注册任务状态监听。使用Promise异步回调。 |
| [on](arkts-ability-missionmanager-on-f-sys.md#on-1) | 注册系统任务状态监听器。 |
| [unlockMission](arkts-ability-missionmanager-unlockmission-f-sys.md#unlockmission-1) | 解锁指定任务ID的任务。使用callback异步回调。 |
| [unlockMission](arkts-ability-missionmanager-unlockmission-f-sys.md#unlockmission-2) | 解锁指定任务ID的任务。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MissionInfo](arkts-ability-missionmanager-missioninfo-t-sys.md) | 表示任务的详细信息。 |
| [MissionListener](arkts-ability-missionmanager-missionlistener-t-sys.md) | 定义系统任务状态监听。 |
| [MissionSnapshot](arkts-ability-missionmanager-missionsnapshot-t-sys.md) | 任务的任务快照对象。 |
<!--DelEnd-->

