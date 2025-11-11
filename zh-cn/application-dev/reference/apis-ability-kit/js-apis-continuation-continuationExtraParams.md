# ContinuationExtraParams
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @huipeizi-->

流转管理入口中设备选择模块所需的过滤参数，可以作为[startContinuationDeviceManager](js-apis-continuation-continuationManager.md#continuationmanagerstartcontinuationdevicemanagerdeprecated)的入参。

> **说明：**
> 
> 本模块首批接口从API version 8开始支持，从API version 22开始不再维护，建议使用[分布式设备管理](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md)替代。

## ContinuationExtraParams<sup>(deprecated)</sup>

表示流转管理入口中设备选择模块所需的过滤参数。

> **说明：**
> 
> 从API version 22开始不再维护，建议使用[devicebasicinfo](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#devicebasicinfo)代替。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：以下各项对应的系统能力均为SystemCapability.Ability.DistributedAbilityManager

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| deviceType | Array\<string> | 否 | 是 | 表示设备类型。|
| targetBundle | string | 否 | 是 | 表示目标Bundle名称。 |
| description | string | 否 | 是 | 表示设备过滤的描述。 |
| filter | any | 否 | 是 | 表示设备过滤的参数。 |
| continuationMode | [continuationManager.ContinuationMode](js-apis-continuation-continuationManager.md#continuationmodedeprecated) | 否 | 是 | 表示协同的模式。 |
| authInfo | Record<string, Object> | 否 | 是 | 表示认证的信息。 |