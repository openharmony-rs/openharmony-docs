# MissionDeviceInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=1e357e1a9db0c5699e6a05a0f31a4e4d2907a0a5 translatedAt=2026-09-03T11:58:42.807Z pushedAt=2026-09-05T10:47:30.825Z -->

Can be used as an input parameter of [registerMissionListener](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerregistermissionlistener) to represent the object of the parameters required for registering a listener.

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

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed services.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| deviceId | string | No   | No   | Device ID.|
