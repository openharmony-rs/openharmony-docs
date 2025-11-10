# ContinuationResult
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @huipeizi-->

流转管理入口返回的设备信息。

> **说明：**
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## ContinuationResult<sup>(deprecated)</sup>

ContinuationManager的[on](js-apis-continuation-continuationManager.md#continuationmanagerondeviceselecteddeprecated)接口返回此对象表示流转管理入口返回的设备信息。

> **说明：**
> 
> 从API version 8开始支持，从API version 22开始不再维护，由于接口定义存在功能重复，请统一使用[分布式设备管理](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md)相关接口。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：以下各项对应的系统能力均为SystemCapability.Ability.DistributedAbilityManager

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| id | string | 否 | 否 | 表示设备标识。|
| type | string | 否 | 否 | 表示设备类型。 |
| name | string | 否 | 否 | 表示设备名称。 |