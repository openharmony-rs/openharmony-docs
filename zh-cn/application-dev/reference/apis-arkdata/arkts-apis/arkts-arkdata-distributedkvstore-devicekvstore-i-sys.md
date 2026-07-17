# DeviceKVStore

设备协同数据库，继承自SingleKVStore，提供查询数据和端端同步数据的方法，可以使用SingleKVStore的方法例如：put、putBatch等。

设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。

比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。

在调用DeviceKVStore的方法前，需要先通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore-1)构建一个DeviceKVStore实例。

**继承/实现关系：** DeviceKVStore extends [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md)

**起始版本：** 9

<!--Device-distributedKVStore-interface DeviceKVStore extends SingleKVStore--><!--Device-distributedKVStore-interface DeviceKVStore extends SingleKVStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## getResultSet

```TypeScript
getResultSet(predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<KVStoreResultSet>): void
```

获取与指定Predicates对象匹配的KVStoreResultSet对象，使用callback异步回调。获取结果集后，需要及时调用closeResultSet方法关闭结果集以释放资源。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件，不允许为null。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<KVStoreResultSet> | 是 | Promise对象。返回KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

## getResultSet

```TypeScript
getResultSet(predicates: dataSharePredicates.DataSharePredicates): Promise<KVStoreResultSet>
```

获取与指定Predicates对象匹配的KVStoreResultSet对象，使用Promise异步回调。获取结果集后，需要及时调用closeResultSet方法关闭结果集以释放资源。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(predicates: dataSharePredicates.DataSharePredicates): Promise<KVStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(predicates: dataSharePredicates.DataSharePredicates): Promise<KVStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件，不允许为null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<KVStoreResultSet> | Promise对象。返回KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

## getResultSet

```TypeScript
getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<KVStoreResultSet>): void
```

获取与本设备指定Predicates对象匹配的KVStoreResultSet对象，使用callback异步回调。获取结果集后，需要及时调用closeResultSet方法关闭结果集以释放资源。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | Indicates the ID of the device to which the results belong. |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件，不允许为null。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<KVStoreResultSet> | 是 | 回调函数，获取与指定Predicates对象匹配的KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

## getResultSet

```TypeScript
getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates): Promise<KVStoreResultSet>
```

获取与本设备指定Predicates对象匹配的KVStoreResultSet对象，使用Promise异步回调。获取结果集后，需要及时调用closeResultSet方法关闭结果集以释放资源。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceKVStore-getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates): Promise<KVStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates): Promise<KVStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Provider

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | Indicates the ID of the device to which the results belong. |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 指示筛选条件，不允许为null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<KVStoreResultSet> | Promise对象。返回KVStoreResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits.<br>**适用版本：** 10+ |

