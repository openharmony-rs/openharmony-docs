# @ohos.security.asset

关键资产存储服务提供了用户短敏感数据的安全存储及管理能力。其中，短敏感数据可以是密码类（账号/密码）、Token类（应用凭据）、其他关键明文（如银行卡号）等长度较短的用户敏感数据。

**起始版本：** 11

**系统能力：** SystemCapability.Security.Asset

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [add](arkts-assetstore-asset-add-f.md#add-1) | 新增一条关键资产。使用Promise异步回调。<br/><br/>设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性时，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考<br/>[声明权限](../../../../security/AccessToken/declare-permissions.md)。<br/> |
| <!--DelRow-->[addAsUser](arkts-assetstore-asset-addasuser-f-sys.md#addAsUser-1) | 在指定用户空间中新增一条关键资产。使用Promise异步回调。<br/><br/>设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性，需申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参<br/>考[声明权限](../../../../security/AccessToken/declare-permissions.md)。<br/> |
| [addSync](arkts-assetstore-asset-addsync-f.md#addSync-1) | 新增一条关键资产，使用同步方式返回结果。<br/><br/>如果要设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考<br/>[声明权限](../../../../security/AccessToken/declare-permissions.md)。<br/> |
| [batchAdd](arkts-assetstore-asset-batchadd-f.md#batchAdd-1) | 批量新增关键资产。使用Promise异步回调。<br/><br/>设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性时，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考<br/>[声明权限](../../../../security/AccessToken/declare-permissions.md)。<br/><br/>批量新增的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。<br/><br/>批量新增的关键资产数量最大值为100。<br/> |
| [batchRemove](arkts-assetstore-asset-batchremove-f.md#batchRemove-1) | 批量删除符合条件的关键资产。使用Promise异步回调。<br/><br/>批量删除的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。<br/><br/>批量删除的关键资产数量最大值为100。<br/> |
| [batchUpdate](arkts-assetstore-asset-batchupdate-f.md#batchUpdate-1) | 批量更新符合条件的关键资产。使用Promise异步回调。<br/><br/>批量更新的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。<br/><br/>批量更新的关键资产数量最大值为100。<br/> |
| [postQuery](arkts-assetstore-asset-postquery-f.md#postQuery-1) | 查询的后置处理，用于需要用户认证的关键资产（与[asset.preQuery](arkts-assetstore-asset-prequery-f.md#preQuery-1)函数成对出现）。使用Promise异步回调。<br/> |
| <!--DelRow-->[postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser-1) | 在指定用户空间中查询的后置处理，用于需要用户认证的关键资产（与[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser-1)函数成对出现）。使用Promise异步回调。<br/> |
| [postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync-1) | 查询的后置处理，用于需要用户认证的关键资产。需与[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync-1)函数成对出现。使用同步方式返回结果。<br/> |
| [preQuery](arkts-assetstore-asset-prequery-f.md#preQuery-1) | 查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.query](arkts-assetstore-asset-query-f.md#query-1)和[asset.postQuery](arkts-assetstore-asset-postquery-f.md#postQuery-1)接口。使用<br/>Promise异步回调。<br/> |
| <!--DelRow-->[preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser-1) | 在指定用户空间中查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md#queryAsUser-1)和<br/>[asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser-1)接口。使用Promise异步回调。<br/> |
| [preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync-1) | 查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.querySync](arkts-assetstore-asset-querysync-f.md#querySync-1)、<br/>[asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync-1)。使用同步方式返回结果。<br/> |
| [query](arkts-assetstore-asset-query-f.md#query-1) | 查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuery](arkts-assetstore-asset-prequery-f.md#preQuery-1)接口，在本函数后调用<br/>[asset.postQuery](arkts-assetstore-asset-postquery-f.md#postQuery-1)接口，开发步骤请参考[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使<br/>用Promise异步回调。<br/><br/>如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。<br/> |
| <!--DelRow-->[queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md#queryAsUser-1) | 在指定用户空间中查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser-1)接口，在本函数后调用<br/>[asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser-1)接口，开发步骤请参考<br/>[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用Promise异步回调。<br/> |
| [querySync](arkts-assetstore-asset-querysync-f.md#querySync-1) | 查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync-1)，在本函数后调用<br/>[asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync-1)，开发步骤请参考<br/>[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用同步方式返回结果。<br/><br/>如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。<br/> |
| [querySyncResult](arkts-assetstore-asset-querysyncresult-f.md#querySyncResult-1) | 执行同步操作后，查询同步执行结果。使用Promise异步回调。<br/> |
| [remove](arkts-assetstore-asset-remove-f.md#remove-1) | 删除符合条件的一条或多条关键资产。使用Promise异步回调。<br/> |
| <!--DelRow-->[removeAsUser](arkts-assetstore-asset-removeasuser-f-sys.md#removeAsUser-1) | 从指定用户空间中删除符合条件的一条或多条关键资产。使用Promise异步回调。<br/> |
| [removeSync](arkts-assetstore-asset-removesync-f.md#removeSync-1) | 删除符合条件的一条或多条关键资产，使用同步方式。<br/> |
| [update](arkts-assetstore-asset-update-f.md#update-1) | 更新符合条件的一条关键资产。使用Promise异步回调。<br/> |
| <!--DelRow-->[updateAsUser](arkts-assetstore-asset-updateasuser-f-sys.md#updateAsUser-1) | 在指定用户空间中更新符合条件的一条关键资产。使用Promise异步回调。<br/> |
| [updateSync](arkts-assetstore-asset-updatesync-f.md#updateSync-1) | 更新符合条件的一条关键资产，使用同步方式返回结果。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BatchErrInfo](arkts-assetstore-asset-batcherrinfo-i.md) | 批量操作中单个关键资产的错误信息。<br/> |
| [BatchResult](arkts-assetstore-asset-batchresult-i.md) | [batchAdd](arkts-assetstore-asset-batchadd-f.md#batchAdd-1)、[batchUpdate](arkts-assetstore-asset-batchupdate-f.md#batchUpdate-1)和[batchRemove](arkts-assetstore-asset-batchremove-f.md#batchRemove-1)批量操作的<br/>结果。<br/> |
| [SyncResult](arkts-assetstore-asset-syncresult-i.md) | 关键资产同步的结果。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Accessibility](arkts-assetstore-asset-accessibility-e.md) | 枚举，关键资产基于锁屏状态的访问控制类型。<br/> |
| [AuthType](arkts-assetstore-asset-authtype-e.md) | 枚举，关键资产支持的用户认证类型。<br/> |
| <!--DelRow-->[AuthType](arkts-assetstore-asset-authtype-e-sys.md) | 枚举，关键资产支持的用户认证类型。<br/> |
| [ConflictResolution](arkts-assetstore-asset-conflictresolution-e.md) | 枚举，新增关键资产时的冲突（如：别名相同）处理策略。<br/> |
| [ErrorCode](arkts-assetstore-asset-errorcode-e.md) | 表示错误码的枚举。<br/> |
| [OperationType](arkts-assetstore-asset-operationtype-e.md) | 枚举，附属的操作类型。<br/> |
| [ReturnType](arkts-assetstore-asset-returntype-e.md) | 枚举，关键资产查询返回的结果类型。<br/> |
| [SyncType](arkts-assetstore-asset-synctype-e.md) | 枚举，关键资产支持的同步类型。<br/> |
| [Tag](arkts-assetstore-asset-tag-e.md) | 枚举，关键资产支持的属性名称类型，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md#AssetMap)的键。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 以下为Tag类型的全量枚举值，每个接口可传的Tag枚举及对应的Value取值范围不同，详见<br/>&gt; [各个场景的开发指导](../../../../security/AssetStoreKit/asset-store-kit-overview.md)。<br/> |
| [TagType](arkts-assetstore-asset-tagtype-e.md) | 枚举，关键资产属性支持的数据类型。<br/> |
| [WrapType](arkts-assetstore-asset-wraptype-e.md) | 枚举，关键资产支持的加密导入导出类型。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 关键资产属性的键-值对集合。<br/> |
| [Value](arkts-assetstore-asset-value-t.md) | 关键资产属性的内容，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md#AssetMap)的值。<br/> |

