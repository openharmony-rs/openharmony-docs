# ContinueMissionInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=0b84378c28775bf03ed39066af758f795e10d166 translatedAt=2026-09-03T11:55:33.625Z pushedAt=2026-09-05T10:47:30.723Z -->

Indicates the interface object of the parameters required for initiating a mission migration by bundle name. For details about mission migration, see [continueMission API](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.
>
> The APIs of this module can be used only in the stage model.

## Properties

**Device behavior difference:** This API does not take effect on wearable devices that do not support distributed services.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| srcDeviceId | string | No   | No   | ID of the source device.|
| dstDeviceId | string | No   | No   | ID of the target device.|
| bundleName | string | No    | No    | Indicates the mission bundle name of the target application. The maximum length is 255 characters. This parameter is used as the default value of srcBundleName. |
| wantParam | Record<string, Object> | No    | No    | Indicates the extended parameters. It is used to pass custom information during mission migration. It can contain developer-defined key-value pairs used to identify the migration scenario or carry migration-related configuration information. |
| srcBundleName<sup>12+</sup> | string | No    | Yes    | Indicates the mission bundle name of the source application. It must be passed in when the source and target application bundle names are different (for example, cross-application migration or application bundle name change). If it is not passed in, it defaults to the same value as bundleName. The maximum length is 255 characters. |
| continueType<sup>12+</sup> | string | No    | Yes    | Indicates the migration type of the application to which the mission belongs. If it is not passed in, the system default value is used. |
