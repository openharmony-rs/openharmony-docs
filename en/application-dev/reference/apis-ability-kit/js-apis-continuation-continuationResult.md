# ContinuationResult
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @huipeizi-->

The ContinuationResult module describes the device information returned by the continuation management entry.

> **NOTE**
> The initial APIs of this module are supported since API version 8 and deprecated since API version 22. You are advised to use the APIs in [Distributed Device Management](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md).

## ContinuationResult<sup>(deprecated)</sup>

Describes the device information returned by the continuation management entry after [on](js-apis-continuation-continuationManager.md#continuationmanagerondeviceselecteddeprecated) is called.

> **NOTE**
> 
> This API is deprecated since API version 22. You are advised to use [devicebasicinfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.DistributedAbilityManager

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| id | string | No| No| Device ID.|
| type | string | No| No| Device type.|
| name | string | No| No| Device name.|
