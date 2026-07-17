# MissionCallback（系统接口）

任务回调已注册

**起始版本：** 9

<!--Device-unnamed-export interface MissionCallback--><!--Device-unnamed-export interface MissionCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## notifyMissionsChanged

```TypeScript
notifyMissionsChanged: NotifyMissionsChangedCallback
```

任务变更时由系统调用。

**类型：** NotifyMissionsChangedCallback

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MissionCallback-notifyMissionsChanged: NotifyMissionsChangedCallback--><!--Device-MissionCallback-notifyMissionsChanged: NotifyMissionsChangedCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## notifyNetDisconnect

```TypeScript
notifyNetDisconnect: NotifyNetDisconnectCallback
```

Called by system when network disconnect.

**类型：** NotifyNetDisconnectCallback

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MissionCallback-notifyNetDisconnect: NotifyNetDisconnectCallback--><!--Device-MissionCallback-notifyNetDisconnect: NotifyNetDisconnectCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## notifySnapshot

```TypeScript
notifySnapshot: NotifySnapshotCallback
```

快照发生更改时，系统会调用此函数。

**类型：** NotifySnapshotCallback

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MissionCallback-notifySnapshot: NotifySnapshotCallback--><!--Device-MissionCallback-notifySnapshot: NotifySnapshotCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

