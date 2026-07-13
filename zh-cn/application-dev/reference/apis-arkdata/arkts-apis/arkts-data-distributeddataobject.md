# @ohos.data.distributedDataObject

本模块提供管理基本数据对象的相关能力，包括创建、查询、删除、修改、订阅等；同时支持相同应用多设备间的分布式数据对象协同能力。分布式数据对象处理数据时，不会解析用户数据的内容，存储路径安全性较低，不建议传输个人敏感数据和隐私数据。

**起始版本：** 8

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkdata-create-f.md#create-1) | 创建一个分布式数据对象。对象属性支持基本类型（数字类型、布尔类型和字符串类型）以及复杂类型（数组、基本类型嵌套）。 |
| [createDistributedObject](arkts-arkdata-createdistributedobject-f.md#createdistributedobject-1) | 创建一个分布式数据对象。 |
| [genSessionId](arkts-arkdata-gensessionid-f.md#gensessionid-1) | 随机创建一个sessionId。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BindInfo](arkts-arkdata-bindinfo-i.md) | 数据库的绑定信息。当前版本只支持关系型数据库的绑定。 |
| [DataObject](arkts-arkdata-dataobject-i.md) | 表示一个分布式数据对象。在使用以下接口前，需调用[create()](arkts-arkdata-create-f.md#create-1)获取DataObject对象。 |
| [DistributedObject](arkts-arkdata-distributedobject-i.md) | 表示一个分布式数据对象。在使用以下接口前，需调用[createDistributedObject()](arkts-arkdata-createdistributedobject-f.md#createdistributedobject-1)获取DistributedObject对象。 |
| [RevokeSaveSuccessResponse](arkts-arkdata-revokesavesuccessresponse-i.md) | [revokeSave](arkts-arkdata-dataobject-i.md#revokesave-1)接口回调信息。 |
| [SaveSuccessResponse](arkts-arkdata-savesuccessresponse-i.md) | [save](arkts-arkdata-dataobject-i.md#save-1)接口回调信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataObserver](arkts-arkdata-dataobserver-t.md) | 定义获取分布式对象数据变更的监听回调函数。 |
| [ProgressObserver](arkts-arkdata-progressobserver-t.md) | 定义传输进度的监听回调函数。 |
| [StatusObserver](arkts-arkdata-statusobserver-t.md) | 定义获取分布式对象状态变更的监听回调函数。 |

