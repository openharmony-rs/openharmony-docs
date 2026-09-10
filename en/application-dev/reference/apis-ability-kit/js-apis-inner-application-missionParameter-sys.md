# MissionParameter (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=d87b1aca1fe0f3ca5e5d103ab386c792109de81e translatedAt=2026-09-03T12:00:27.667Z pushedAt=2026-09-05T10:47:30.848Z -->

Serves as an input parameter of [startSyncRemoteMissions](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerstartsyncremotemissions), representing the interface of the parameters required for sync.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { distributedMissionManager } from '@kit.AbilityKit';
```

## MissionParameter

**Device behavior differences** This API does not take effect on Wearable devices that do not support distributed services.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name         | Type   | Read-Only  | Optional  | Description         |
| ----------- | ------- | ---- | ---- | ----------- |
| deviceId    | string  | No    | No    | ID of the target device for sync.     |
| fixConflict | boolean | No    | No    | Whether to handle version conflicts. The value true means to handle conflicts, and false means not to handle conflicts. |
| tag         | number  | No    | No    | Tag of the mission, which is a non-negative integer. The value 0 indicates the default tag, used to identify and distinguish different sync missions.    |
