# @ohos.app.ability.missionManager

/*
 Copyright (c) 2022-2023 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License"),
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace missionManager--><!--Device-unnamed-declare namespace missionManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md#clearAllMissions) | 清理所有未锁定的任务。使用callback异步回调。 |
| [clearAllMissions](arkts-ability-missionmanager-clearallmissions-f-sys.md#clearAllMissions（系统接口）) | 清理所有未锁定的任务。使用Promise异步回调。 |
| [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md#clearMission) | 清理指定任务ID的任务，无论该任务是否被锁定。使用callback异步回调。 |
| [clearMission](arkts-ability-missionmanager-clearmission-f-sys.md#clearMission（系统接口）) | 清理指定任务ID的任务，无论该任务是否被锁定。使用Promise异步回调。 |
| [getLowResolutionMissionSnapShot](arkts-ability-missionmanager-getlowresolutionmissionsnapshot-f-sys.md#getLowResolutionMissionSnapShot) | 获取任务低分辨率快照。使用callback异步回调。 |
| [getLowResolutionMissionSnapShot](arkts-ability-missionmanager-getlowresolutionmissionsnapshot-f-sys.md#getLowResolutionMissionSnapShot（系统接口）) | 获取任务低分辨率快照。使用Promise异步回调。 |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getMissionInfo) | 获取任务信息。使用callback异步回调。 |
| [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getMissionInfo（系统接口）) | 获取任务信息。使用Promise异步回调。 |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getMissionInfos) | 获取所有任务信息。使用callback异步回调。 |
| [getMissionInfos](arkts-ability-missionmanager-getmissioninfos-f-sys.md#getMissionInfos（系统接口）) | 获取所有任务信息。使用Promise异步回调。 |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md#getMissionSnapShot) | 获取任务快照。使用callback异步回调。 |
| [getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md#getMissionSnapShot（系统接口）) | 获取任务快照。使用Promise异步回调。 |
| [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md#lockMission) | 锁定指定任务ID的任务。使用callback异步回调。 |
| [lockMission](arkts-ability-missionmanager-lockmission-f-sys.md#lockMission（系统接口）) | 锁定指定任务ID的任务。使用Promise异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#moveMissionToFront) | 把指定任务ID的任务切到前台。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#moveMissionToFront（系统接口）) | 把指定任务ID的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。 |
| [moveMissionToFront](arkts-ability-missionmanager-movemissiontofront-f-sys.md#moveMissionToFront（系统接口）) | 把指定任务ID的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。 |
| [moveMissionsToBackground](arkts-ability-missionmanager-movemissionstobackground-f-sys.md#moveMissionsToBackground) | 将指定任务批量切到后台，返回的结果任务ID按被隐藏时的任务层级排序。使用callback异步回调。 |
| [moveMissionsToBackground](arkts-ability-missionmanager-movemissionstobackground-f-sys.md#moveMissionsToBackground（系统接口）) | 将指定任务批量切到后台，返回的结果按被隐藏时的任务层级排序。使用Promise异步回调。 |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#moveMissionsToForeground) | 将指定任务批量切到前台。使用callback异步回调。 |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#moveMissionsToForeground（系统接口）) | 将指定任务批量切换到前台，并将任务ID等于topMission的任务移动到最顶层。使用callback异步回调。 |
| [moveMissionsToForeground](arkts-ability-missionmanager-movemissionstoforeground-f-sys.md#moveMissionsToForeground（系统接口）) | 将指定任务批量切到前台，并将任务ID等于topMission的任务移动到最顶层。使用Promise异步回调。 |
| [offMission](arkts-ability-missionmanager-offmission-f-sys.md#offMission) | 解注册任务状态监听器。使用callback异步回调。 |
| [offMission](arkts-ability-missionmanager-offmission-f-sys.md#offMission（系统接口）) | 解注册任务状态监听。使用Promise异步回调。 |
| off_mission | 解注册任务状态监听器。使用callback异步回调。 |
| [off_mission](arkts-ability-missionmanager-offmission-f-sys.md#off_mission-1) | 解注册任务状态监听。使用Promise异步回调。 |
| [onMission](arkts-ability-missionmanager-onmission-f-sys.md#onMission) | 注册系统任务状态监听器。 |
| on_mission | 注册系统任务状态监听器。 |
| [unlockMission](arkts-ability-missionmanager-unlockmission-f-sys.md#unlockMission) | 解锁指定任务ID的任务。使用callback异步回调。 |
| [unlockMission](arkts-ability-missionmanager-unlockmission-f-sys.md#unlockMission（系统接口）) | 解锁指定任务ID的任务。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MissionInfo](arkts-ability-missionmanager-missioninfo-t-sys.md) | 表示任务的详细信息。 |
| [MissionListener](arkts-ability-missionmanager-missionlistener-t-sys.md) | 定义系统任务状态监听。 |
| [MissionSnapshot](arkts-ability-missionmanager-missionsnapshot-t-sys.md) | 任务的任务快照对象。 |
<!--DelEnd-->

