# @ohos.security.asset

关键资产存储服务提供了用户短敏感数据的安全存储及管理能力。其中，短敏感数据可以是密码类（账号/密码）、Token类（应用凭据）、其他关键明文（如银行卡号）等长度较短的用户敏感数据。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Asset

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [add](arkts-assetstore-add-f.md#add-1) | 新增一条关键资产。使用Promise异步回调。设置[Tag.IS_PERSISTENT](arkts-assetstore-tagtype-e.md)属性时，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考[声明权限](../../../../security/AccessToken/declare-permissions.md)。 |
| [addSync](arkts-assetstore-addsync-f.md#addsync-1) | 新增一条关键资产，使用同步方式返回结果。如果要设置[Tag.IS_PERSISTENT](arkts-assetstore-tagtype-e.md)属性，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考[声明权限](../../../../security/AccessToken/declare-permissions.md)。 |
| [batchAdd](arkts-assetstore-batchadd-f.md#batchadd-1) | 批量新增关键资产。使用Promise异步回调。设置[Tag.IS_PERSISTENT](arkts-assetstore-tagtype-e.md)属性时，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考[声明权限](../../../../security/AccessToken/declare-permissions.md)。批量新增的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-tagtype-e.md)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-tagtype-e.md)属性。批量新增的关键资产数量最大值为100。 |
| [batchRemove](arkts-assetstore-batchremove-f.md#batchremove-1) | 批量删除符合条件的关键资产。使用Promise异步回调。批量删除的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-tagtype-e.md)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-tagtype-e.md)属性。批量删除的关键资产数量最大值为100。 |
| [batchUpdate](arkts-assetstore-batchupdate-f.md#batchupdate-1) | 批量更新符合条件的关键资产。使用Promise异步回调。批量更新的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-tagtype-e.md)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-tagtype-e.md)属性。批量更新的关键资产数量最大值为100。 |
| [postQuery](arkts-assetstore-postquery-f.md#postquery-1) | 查询的后置处理，用于需要用户认证的关键资产（与[asset.preQuery](arkts-assetstore-prequery-f.md#prequery-1)函数成对出现）。使用Promise异步回调。 |
| [postQuerySync](arkts-assetstore-postquerysync-f.md#postquerysync-1) | 查询的后置处理，用于需要用户认证的关键资产。需与[asset.preQuerySync](arkts-assetstore-prequerysync-f.md#prequerysync-1)函数成对出现。使用同步方式返回结果。 |
| [preQuery](arkts-assetstore-prequery-f.md#prequery-1) | 查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.query](arkts-assetstore-query-f.md#query-1)和[asset.postQuery](arkts-assetstore-postquery-f.md#postquery-1)接口。使用Promise异步回调。 |
| [preQuerySync](arkts-assetstore-prequerysync-f.md#prequerysync-1) | 查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.querySync](arkts-assetstore-querysync-f.md#querysync-1)、[asset.postQuerySync](arkts-assetstore-postquerysync-f.md#postquerysync-1)。使用同步方式返回结果。 |
| [query](arkts-assetstore-query-f.md#query-1) | 查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuery](arkts-assetstore-prequery-f.md#prequery-1)接口，在本函数后调用[asset.postQuery](arkts-assetstore-postquery-f.md#postquery-1)接口，开发步骤请参考[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用Promise异步回调。如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。 |
| [querySync](arkts-assetstore-querysync-f.md#querysync-1) | 查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuerySync](arkts-assetstore-prequerysync-f.md#prequerysync-1)，在本函数后调用[asset.postQuerySync](arkts-assetstore-postquerysync-f.md#postquerysync-1)，开发步骤请参考[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用同步方式返回结果。如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。 |
| [querySyncResult](arkts-assetstore-querysyncresult-f.md#querysyncresult-1) | 执行同步操作后，查询同步执行结果。使用Promise异步回调。 |
| [remove](arkts-assetstore-remove-f.md#remove-1) | 删除符合条件的一条或多条关键资产。使用Promise异步回调。 |
| [removeSync](arkts-assetstore-removesync-f.md#removesync-1) | 删除符合条件的一条或多条关键资产，使用同步方式。 |
| [update](arkts-assetstore-update-f.md#update-1) | 更新符合条件的一条关键资产。使用Promise异步回调。 |
| [updateSync](arkts-assetstore-updatesync-f.md#updatesync-1) | 更新符合条件的一条关键资产，使用同步方式返回结果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAsUser](arkts-assetstore-addasuser-f-sys.md#addasuser-1) | 在指定用户空间中新增一条关键资产。使用Promise异步回调。设置[Tag.IS_PERSISTENT](arkts-assetstore-tagtype-e.md)属性，需申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考[声明权限](../../../../security/AccessToken/declare-permissions.md)。 |
| [postQueryAsUser](arkts-assetstore-postqueryasuser-f-sys.md#postqueryasuser-1) | 在指定用户空间中查询的后置处理，用于需要用户认证的关键资产（与[asset.preQueryAsUser](arkts-assetstore-prequeryasuser-f-sys.md#prequeryasuser-1)函数成对出现）。使用Promise异步回调。 |
| [preQueryAsUser](arkts-assetstore-prequeryasuser-f-sys.md#prequeryasuser-1) | 在指定用户空间中查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.queryAsUser](arkts-assetstore-queryasuser-f-sys.md#queryasuser-1)和[asset.postQueryAsUser](arkts-assetstore-postqueryasuser-f-sys.md#postqueryasuser-1)接口。使用Promise异步回调。 |
| [queryAsUser](arkts-assetstore-queryasuser-f-sys.md#queryasuser-1) | 在指定用户空间中查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQueryAsUser](arkts-assetstore-prequeryasuser-f-sys.md#prequeryasuser-1)接口，在本函数后调用[asset.postQueryAsUser](arkts-assetstore-postqueryasuser-f-sys.md#postqueryasuser-1)接口，开发步骤请参考[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用Promise异步回调。 |
| [removeAsUser](arkts-assetstore-removeasuser-f-sys.md#removeasuser-1) | 从指定用户空间中删除符合条件的一条或多条关键资产。使用Promise异步回调。 |
| [updateAsUser](arkts-assetstore-updateasuser-f-sys.md#updateasuser-1) | 在指定用户空间中更新符合条件的一条关键资产。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BatchErrInfo](arkts-assetstore-batcherrinfo-i.md) | 批量操作中单个关键资产的错误信息。 |
| [BatchResult](arkts-assetstore-batchresult-i.md) | [batchAdd](arkts-assetstore-batchadd-f.md#batchadd-1)、[batchUpdate](arkts-assetstore-batchupdate-f.md#batchupdate-1)和[batchRemove](arkts-assetstore-batchremove-f.md#batchremove-1)批量操作的结果。 |
| [SyncResult](arkts-assetstore-syncresult-i.md) | 关键资产同步的结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Accessibility](arkts-assetstore-accessibility-e.md) | 枚举，关键资产基于锁屏状态的访问控制类型。 |
| [AuthType](arkts-assetstore-authtype-e.md) | 枚举，关键资产支持的用户认证类型。 |
| [ConflictResolution](arkts-assetstore-conflictresolution-e.md) | 枚举，新增关键资产时的冲突（如：别名相同）处理策略。 |
| [ErrorCode](arkts-assetstore-errorcode-e.md) | 表示错误码的枚举。 |
| [OperationType](arkts-assetstore-operationtype-e.md) | 枚举，附属的操作类型。 |
| [ReturnType](arkts-assetstore-returntype-e.md) | 枚举，关键资产查询返回的结果类型。 |
| [SyncType](arkts-assetstore-synctype-e.md) | 枚举，关键资产支持的同步类型。 |
| [Tag](arkts-assetstore-tag-e.md) | 枚举，关键资产支持的属性名称类型，用作[AssetMap](arkts-assetstore-assetmap-t.md)的键。 |
| [TagType](arkts-assetstore-tagtype-e.md) | 枚举，关键资产属性支持的数据类型。 |
| [WrapType](arkts-assetstore-wraptype-e.md) | 枚举，关键资产支持的加密导入导出类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthType](arkts-assetstore-authtype-e-sys.md) | 枚举，关键资产支持的用户认证类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AssetMap](arkts-assetstore-assetmap-t.md) | 关键资产属性的键-值对集合。 |
| [Value](arkts-assetstore-value-t.md) | 关键资产属性的内容，用作[AssetMap](arkts-assetstore-assetmap-t.md)的值。 |

