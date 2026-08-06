# @ohos.data.sendableRelationalStore

该模块针对关系型数据库（Relational Database，RDB）提供了sendable支持。支持从查询结果集中获取sendable类型ValuesBucket用于并发实例间传递。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare namespace sendableRelationalStore--><!--Device-unnamed-declare namespace sendableRelationalStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [fromSendableAsset](arkts-arkdata-sendablerelationalstore-fromsendableasset-f.md#fromsendableasset) | 将可跨线程传递的附件数据，转换为不可跨线程传递的附件数据。 |
| [fromSendableValues](arkts-arkdata-sendablerelationalstore-fromsendablevalues-f.md#fromsendablevalues) | 将可跨线程传递的数组数据，转换为不可跨线程传递的数组数据。 |
| [fromSendableValuesBucket](arkts-arkdata-sendablerelationalstore-fromsendablevaluesbucket-f.md#fromsendablevaluesbucket) | 将可用于跨线程传递的键值对数据，转换为不能用于跨线程传递的键值对数据。 |
| [toSendableAsset](arkts-arkdata-sendablerelationalstore-tosendableasset-f.md#tosendableasset) | 将不可跨线程传递的附件数据，转换为可跨线程传递的附件数据。 |
| [toSendableValues](arkts-arkdata-sendablerelationalstore-tosendablevalues-f.md#tosendablevalues) | 将不可跨线程传递的数组数据，转换为可跨线程传递的数组数据。 |
| [toSendableValuesBucket](arkts-arkdata-sendablerelationalstore-tosendablevaluesbucket-f.md#tosendablevaluesbucket) | 将不能用于跨线程传递的键值对数据，转换为可用于跨线程传递的键值对数据。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Asset](arkts-arkdata-sendablerelationalstore-asset-i.md) | 记录资产附件（文件、图片、视频等类型文件）的相关信息。用于支持资产数据跨线程传递，继承自 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。资产类型的相关接口暂不支持Datashare。使用 [sendableRelationalStore.toSendableAsset]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法创建。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Assets](arkts-arkdata-sendablerelationalstore-assets-t.md) | 表示[Asset]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_类型数据的集合。用于支持Asset数据集合跨线程传递。 |
| [NonSendableAsset](arkts-arkdata-sendablerelationalstore-nonsendableasset-t.md) | 记录资产附件（文件、图片、视频等类型文件）的相关信息。不支持跨线程传递。 |
| [NonSendableBucket](arkts-arkdata-sendablerelationalstore-nonsendablebucket-t.md) | 用于存储键值对的类型。不支持跨线程传递。 |
| [NonSendableValues](arkts-arkdata-sendablerelationalstore-nonsendablevalues-t.md) | 表示[ValueType]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_数据数组存储。不支持跨线程传递。 |
| [ValueType](arkts-arkdata-sendablerelationalstore-valuetype-t.md) | 用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。 |
| [ValuesBucket](arkts-arkdata-sendablerelationalstore-valuesbucket-t.md) | 表示[ValueType]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_数据的键值对存储，用于支持ValueType数据跨线程传递。 |

