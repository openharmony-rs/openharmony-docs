# MissionCallbacks

The module defines the callbacks invoked after synchronization starts. These callbacks can be used as input
 parameters in
 [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md)


## 汇总

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MissionCallback](arkts-ability-missioncallbacks-missioncallback-i-sys.md) | 作为可以[registerMissionListener]的入参，表示开始同步后，建立的回调函数，用于监听任务状态变化，包含任务列表变化通知、任务快照通知和断开连接通知等功能。@interface MissionCallback |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NotifyMissionsChangedCallback](arkts-ability-notifymissionschangedcallback-t-sys.md) |  |
| [NotifyNetDisconnectCallback](arkts-ability-notifynetdisconnectcallback-t-sys.md) |  |
| [NotifySnapshotCallback](arkts-ability-notifysnapshotcallback-t-sys.md) |  |
<!--DelEnd-->
