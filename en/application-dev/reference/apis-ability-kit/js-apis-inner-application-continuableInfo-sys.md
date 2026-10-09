# ContinuableInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=ca2f887e08391e210e2049233bcc8498da06b5a5 translatedAt=2026-09-03T11:54:46.366Z pushedAt=2026-09-05T10:47:30.717Z -->

When the callback for listening to the application task migration state is registered, the application task migration state and migration information are returned. For details about registration, see [distributedMissionManager.on('continueStateChange')](js-apis-distributedMissionManager-sys.md#distributedmissionmanageroncontinuestatechange10).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.
> The APIs of this module can be used only in the stage model.

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed services.

## Modules to Import

```js
import { distributedMissionManager } from '@kit.AbilityKit';
```

## ContinuableInfo

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed services.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name      | Type  | Read-Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| srcDeviceId | string | No    | No    | Indicates the ID of the source device for task migration. |
| bundleName | string | No    | No    | Indicates the bundle name of the target application to which the task belongs. This parameter is used as the default value of srcBundleName. When srcBundleName is not passed in, its value is the same as bundleName by default. |
| srcBundleName<sup>12+</sup> | string | No    | Yes    | Indicates the bundle name of the source application to which the task belongs. This parameter must be passed in when the source and target application bundle names are different (for example, cross-application migration or application bundle name change). If it is not passed in, its value is the same as bundleName by default. |
| continueType<sup>12+</sup> | string | No    | Yes    | Indicates the migration type of the application to which the task belongs. The value is customized by the application in the configuration file and is used to identify different task migration policies (for example, task migration in multi-device collaboration and cross-device task state replication). If this parameter is not passed in, the system default value is used. |
