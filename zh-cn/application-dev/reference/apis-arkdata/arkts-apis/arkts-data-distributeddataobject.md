# @ohos.data.distributedDataObject

本模块提供管理基本数据对象的相关能力，包括创建、查询、删除、修改、订阅等；同时支持相同应用多设备间的分布式数据对象协同能力。分布式数据对象处理数据时，不会解析用户数据的内容，存储路径安全性较低，不建议传输个人敏感数据和隐私数据。

**起始版本：** 8

<!--Device-unnamed-declare namespace distributedDataObject--><!--Device-unnamed-declare namespace distributedDataObject-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

## 导入模块

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkdata-distributeddataobject-create-f.md#create) | 创建一个分布式数据对象。对象属性支持基本类型（数字类型、布尔类型和字符串类型）以及复杂类型（数组、基本类型嵌套）。 |
| [createDistributedObject](arkts-arkdata-distributeddataobject-createdistributedobject-f.md#createdistributedobject) | 创建一个分布式数据对象。 |
| [genSessionId](arkts-arkdata-distributeddataobject-gensessionid-f.md#gensessionid) | 随机创建一个sessionId。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BindInfo](arkts-arkdata-distributeddataobject-bindinfo-i.md) | 数据库的绑定信息。当前版本只支持关系型数据库的绑定。 |
| [DataObject](arkts-arkdata-distributeddataobject-dataobject-i.md) | 表示一个分布式数据对象。在使用以下接口前，需调用[create()](arkts-arkdata-distributeddataobject-create-f.md#create)获取DataObject对象。 |
| [DistributedObject](arkts-arkdata-distributeddataobject-distributedobject-i.md) | 表示一个分布式数据对象。在使用以下接口前，需调用[createDistributedObject()](arkts-arkdata-distributeddataobject-createdistributedobject-f.md#createdistributedobject)获取DistributedObject对象。 |
| [RevokeSaveSuccessResponse](arkts-arkdata-distributeddataobject-revokesavesuccessresponse-i.md) | [revokeSave](arkts-arkdata-distributeddataobject-dataobject-i.md#revokesave)接口回调信息。 |
| [SaveSuccessResponse](arkts-arkdata-distributeddataobject-savesuccessresponse-i.md) | [save](arkts-arkdata-distributeddataobject-dataobject-i.md#save)接口回调信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DataObserver](arkts-arkdata-distributeddataobject-dataobserver-t.md) | 定义获取分布式对象数据变更的监听回调函数。 |
| [ProgressObserver](arkts-arkdata-distributeddataobject-progressobserver-t.md) | 定义传输进度的监听回调函数。 |
| [StatusObserver](arkts-arkdata-distributeddataobject-statusobserver-t.md) | 定义获取分布式对象状态变更的监听回调函数。 |

