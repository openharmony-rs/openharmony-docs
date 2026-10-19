# ContinueDeviceInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=d87b1aca1fe0f3ca5e5d103ab386c792109de81e translatedAt=2026-09-03T11:55:28.141Z pushedAt=2026-09-05T10:47:30.721Z -->

Defines the interface object that represents the parameters required for initiating mission continuation. For details about mission continuation, see [continueMission API](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module are system APIs.
> The APIs of this module can be used only in the stage model.

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| srcDeviceId | string | No | No | ID of the source device for Mission migration. |
| dstDeviceId | string | No | No | ID of the destination device for Mission migration. |
| missionId | number | No | No | ID of the Mission migration task. |
| wantParam | Record<string, Object> | No | No | Extended parameters for Mission migration, used to pass custom information during task migration. It can contain developer-defined key-value pairs used to identify the migration scenario or carry migration-related configuration information. |
