# @ohos.application.missionManager

missionManager模块提供系统任务管理能力，包括对系统任务执行锁定、解锁、清理、切换到前台等操作。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** missionManager/missionManager

**需要权限：** ohos.permission.MANAGE_MISSIONS

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[clearAllMissions](arkts-api10lessdeprecatedmodules-missionmanager-clearallmissions-f-sys.md#clearAllMissions-1) | 清理所有未锁定的任务。使用callback异步回调。<br/> |
| <!--DelRow-->[clearAllMissions](arkts-api10lessdeprecatedmodules-missionmanager-clearallmissions-f-sys.md#clearAllMissions-2) | 清理所有未锁定的任务。使用Promise异步回调。<br/> |
| <!--DelRow-->[clearMission](arkts-api10lessdeprecatedmodules-missionmanager-clearmission-f-sys.md#clearMission-1) | 清理指定任务id的任务，无论该任务是否被锁定。使用callback异步回调。<br/> |
| <!--DelRow-->[clearMission](arkts-api10lessdeprecatedmodules-missionmanager-clearmission-f-sys.md#clearMission-2) | 清理指定任务id的任务，无论该任务是否被锁定。使用Promise异步回调。<br/> |
| <!--DelRow-->[getMissionInfo](arkts-api10lessdeprecatedmodules-missionmanager-getmissioninfo-f-sys.md#getMissionInfo-1) | 获取单个任务信息。使用callback异步回调。<br/> |
| <!--DelRow-->[getMissionInfo](arkts-api10lessdeprecatedmodules-missionmanager-getmissioninfo-f-sys.md#getMissionInfo-2) | 获取单个任务信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getMissionInfos](arkts-api10lessdeprecatedmodules-missionmanager-getmissioninfos-f-sys.md#getMissionInfos-1) | 获取所有任务信息。使用callback异步回调。<br/> |
| <!--DelRow-->[getMissionInfos](arkts-api10lessdeprecatedmodules-missionmanager-getmissioninfos-f-sys.md#getMissionInfos-2) | 获取所有任务信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getMissionSnapShot](arkts-api10lessdeprecatedmodules-missionmanager-getmissionsnapshot-f-sys.md#getMissionSnapShot-1) | 获取任务快照。使用callback异步回调。<br/> |
| <!--DelRow-->[getMissionSnapShot](arkts-api10lessdeprecatedmodules-missionmanager-getmissionsnapshot-f-sys.md#getMissionSnapShot-2) | 获取任务快照。使用Promise异步回调。<br/> |
| <!--DelRow-->[lockMission](arkts-api10lessdeprecatedmodules-missionmanager-lockmission-f-sys.md#lockMission-1) | 锁定指定任务id的任务。使用callback异步回调。<br/> |
| <!--DelRow-->[lockMission](arkts-api10lessdeprecatedmodules-missionmanager-lockmission-f-sys.md#lockMission-2) | 锁定指定任务id的任务。使用Promise异步回调。<br/> |
| <!--DelRow-->[moveMissionToFront](arkts-api10lessdeprecatedmodules-missionmanager-movemissiontofront-f-sys.md#moveMissionToFront-1) | 把指定任务id的任务切到前台。使用callback异步回调。<br/> |
| <!--DelRow-->[moveMissionToFront](arkts-api10lessdeprecatedmodules-missionmanager-movemissiontofront-f-sys.md#moveMissionToFront-2) | 把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用callback异步回调。<br/> |
| <!--DelRow-->[moveMissionToFront](arkts-api10lessdeprecatedmodules-missionmanager-movemissiontofront-f-sys.md#moveMissionToFront-3) | 把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等。使用Promise异步回调。<br/> |
| <!--DelRow-->[registerMissionListener](arkts-api10lessdeprecatedmodules-missionmanager-registermissionlistener-f-sys.md#registerMissionListener-1) | 注册系统任务状态监听器。<br/> |
| <!--DelRow-->[unlockMission](arkts-api10lessdeprecatedmodules-missionmanager-unlockmission-f-sys.md#unlockMission-1) | 解锁指定任务id的任务。使用callback异步回调。<br/> |
| <!--DelRow-->[unlockMission](arkts-api10lessdeprecatedmodules-missionmanager-unlockmission-f-sys.md#unlockMission-2) | 解锁指定任务id的任务。使用Promise异步回调。<br/> |
| <!--DelRow-->[unregisterMissionListener](arkts-api10lessdeprecatedmodules-missionmanager-unregistermissionlistener-f-sys.md#unregisterMissionListener-1) | 解注册任务状态监听器。使用callback异步回调。<br/> |
| <!--DelRow-->[unregisterMissionListener](arkts-api10lessdeprecatedmodules-missionmanager-unregistermissionlistener-f-sys.md#unregisterMissionListener-2) | 解注册任务状态监听器。使用Promise异步回调。<br/> |

