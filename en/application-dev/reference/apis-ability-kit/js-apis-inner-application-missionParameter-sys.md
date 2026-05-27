# MissionParameter (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

The module defines the parameters required for mission synchronization. It can be used an input parameter in [startSyncRemoteMissions](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerstartsyncremotemissions).

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

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name         | Type   | Read-Only  | Optional  | Description         |
| ----------- | ------- | ---- | ---- | ----------- |
| deviceId    | string  | No   | No   | Device ID.    |
| fixConflict | boolean | No   | No   | Whether a version conflict exists. **true** if yes, **false** otherwise.|
| tag         | number  | No   | No   | Tag of the mission. The value **0** means the default tag.   |
