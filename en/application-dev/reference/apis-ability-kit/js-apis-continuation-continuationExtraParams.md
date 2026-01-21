# ContinuationExtraParams
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @huipeizi-->

The ContinuationExtraParams module provides the filter parameters required by the device selection module in the continuation management entry. These filter parameters can be used as an input parameter of [startContinuationDeviceManager](js-apis-continuation-continuationManager.md#continuationmanagerstartcontinuationdevicemanagerdeprecated).

> **NOTE**
> 
> The initial APIs of this module have been supported since API version 8 and deprecated since API version 22. You are advised to use the APIs in [Distributed Device Management](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md) instead.

## ContinuationExtraParams<sup>(deprecated)</sup>

Describes the extra parameters required by the device selection module in the continuation management entry.

> **NOTE**
> 
> This API has been deprecated since API version 22. You are advised to use [devicebasicinfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.DistributedAbilityManager

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| deviceType | Array\<string> | No| Yes| Device type.|
| targetBundle | string | No| Yes| Name of the target bundle.|
| description | string | No| Yes| Device filtering description.|
| filter | any | No| Yes| Device filtering parameter.|
| continuationMode | [continuationManager.ContinuationMode](js-apis-continuation-continuationManager.md#continuationmodedeprecated) | No| Yes| Continuation mode.|
| authInfo | Record<string, Object> | No| Yes| Authentication information.|
