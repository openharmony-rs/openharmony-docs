# ContinueMissionInfo (System API)

The module defines the parameters required for initiating mission continuation with the bundle name specified. For details about mission continuation, see [continueMission](js-apis-distributedMissionManager-sys.md#distributedmissionmanagercontinuemission10).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Properties

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| srcDeviceId | string | No   | No   | ID of the source device.|
| dstDeviceId | string | No   | No   | ID of the target device.|
| bundleName | string | No   | No   | Bundle name of the target application to which the mission belongs.|
| wantParam | Record<string, Object> | No   | No   | Extended parameters.|
| srcBundleName<sup>12+</sup> | string | No   | Yes   | Bundle name of the source application to which the mission belongs. The value is the same as that of **bundleName** by default.|
| continueType<sup>12+</sup> | string | No   | Yes   | Continuation type of the application to which the mission belongs.|
