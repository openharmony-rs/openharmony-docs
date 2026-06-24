# MissionDeviceInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

The module defines the parameters required for registering a listener. It can be used as an input parameter in [registerMissionListener](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerregistermissionlistener).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { distributedMissionManager } from '@kit.AbilityKit';
```

## Attributes

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| deviceId | string | No   | No   | Device ID.|
