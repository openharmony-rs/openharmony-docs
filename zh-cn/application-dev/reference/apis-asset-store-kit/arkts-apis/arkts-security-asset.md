# @ohos.security.asset

/*
 Copyright (c) 2024 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare namespace asset--><!--Device-unnamed-declare namespace asset-End-->

**系统能力：** SystemCapability.Security.Asset

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [add](arkts-assetstore-asset-add-f.md#add) | 新增一条关键资产。使用Promise异步回调。 设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性时，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考 [声明权限](../../../security/AccessToken/declare-permissions.md)。 |
| [addSync](arkts-assetstore-asset-addsync-f.md#addSync) | 新增一条关键资产，使用同步方式返回结果。 如果要设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考 [声明权限](../../../security/AccessToken/declare-permissions.md)。 |
| [batchAdd](arkts-assetstore-asset-batchadd-f.md#batchAdd) | 批量新增关键资产。使用Promise异步回调。 设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性时，需要申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参考 [声明权限](../../../security/AccessToken/declare-permissions.md)。 批量新增的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。 批量新增的关键资产数量最大值为100。 |
| [batchRemove](arkts-assetstore-asset-batchremove-f.md#batchRemove) | 批量删除符合条件的关键资产。使用Promise异步回调。 批量删除的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。 批量删除的关键资产数量最大值为100。 |
| [batchUpdate](arkts-assetstore-asset-batchupdate-f.md#batchUpdate) | 批量更新符合条件的关键资产。使用Promise异步回调。 批量更新的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。 批量更新的关键资产数量最大值为100。 |
| [postQuery](arkts-assetstore-asset-postquery-f.md#postQuery) | 查询的后置处理，用于需要用户认证的关键资产（与[asset.preQuery](arkts-assetstore-asset-prequery-f.md#preQuery)函数成对出现）。使用Promise异步回调。 |
| [postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync) | 查询的后置处理，用于需要用户认证的关键资产。需与[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync)函数成对出现。使用同步方式返回结果。 |
| [preQuery](arkts-assetstore-asset-prequery-f.md#preQuery) | 查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.query](arkts-assetstore-asset-query-f.md#query)和[asset.postQuery](arkts-assetstore-asset-postquery-f.md#postQuery)接口。使用 Promise异步回调。 |
| [preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync) | 查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.querySync](arkts-assetstore-asset-querysync-f.md#querySync)、 [asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync)。使用同步方式返回结果。 |
| [query](arkts-assetstore-asset-query-f.md#query) | 查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuery](arkts-assetstore-asset-prequery-f.md#preQuery)接口，在本函数后调用 [asset.postQuery](arkts-assetstore-asset-postquery-f.md#postQuery)接口，开发步骤请参考[开发指导](../../../security/AssetStoreKit/asset-js-query-auth.md)。使 用Promise异步回调。 如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。 |
| [querySync](arkts-assetstore-asset-querysync-f.md#querySync) | 查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync)，在本函数后调用 [asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync)，开发步骤请参考 [开发指导](../../../security/AssetStoreKit/asset-js-query-auth.md)。使用同步方式返回结果。 如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。 |
| [querySyncResult](arkts-assetstore-asset-querysyncresult-f.md#querySyncResult) | 执行同步操作后，查询同步执行结果。使用Promise异步回调。 |
| [remove](arkts-assetstore-asset-remove-f.md#remove) | 删除符合条件的一条或多条关键资产。使用Promise异步回调。 |
| [removeSync](arkts-assetstore-asset-removesync-f.md#removeSync) | 删除符合条件的一条或多条关键资产，使用同步方式。 |
| [update](arkts-assetstore-asset-update-f.md#update) | 更新符合条件的一条关键资产。使用Promise异步回调。 |
| [updateSync](arkts-assetstore-asset-updatesync-f.md#updateSync) | 更新符合条件的一条关键资产，使用同步方式返回结果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAsUser](arkts-assetstore-asset-addasuser-f-sys.md#addAsUser) | 在指定用户空间中新增一条关键资产。使用Promise异步回调。 设置[Tag.IS_PERSISTENT](arkts-assetstore-asset-tagtype-e.md#TagType)属性，需申请ohos.permission.STORE_PERSISTENT_DATA权限，申请方式请参 考[声明权限](../../../security/AccessToken/declare-permissions.md)。 |
| [postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser) | 在指定用户空间中查询的后置处理，用于需要用户认证的关键资产（与[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser（系统接口）)函数成对出现）。使用Promise异步回调。 |
| [preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser) | 在指定用户空间中查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md#queryAsUser（系统接口）)和 [asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser（系统接口）)接口。使用Promise异步回调。 |
| [queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md#queryAsUser) | 在指定用户空间中查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser（系统接口）)接口，在本函数后调用 [asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser（系统接口）)接口，开发步骤请参考 [开发指导](../../../security/AssetStoreKit/asset-js-query-auth.md)。使用Promise异步回调。 |
| [removeAsUser](arkts-assetstore-asset-removeasuser-f-sys.md#removeAsUser) | 从指定用户空间中删除符合条件的一条或多条关键资产。使用Promise异步回调。 |
| [updateAsUser](arkts-assetstore-asset-updateasuser-f-sys.md#updateAsUser) | 在指定用户空间中更新符合条件的一条关键资产。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BatchErrInfo](arkts-assetstore-asset-batcherrinfo-i.md) | 批量操作中单个关键资产的错误信息。 |
| [BatchResult](arkts-assetstore-asset-batchresult-i.md) | [batchAdd](arkts-assetstore-asset-batchadd-f.md#batchAdd)、[batchUpdate](arkts-assetstore-asset-batchupdate-f.md#batchUpdate)和[batchRemove](arkts-assetstore-asset-batchremove-f.md#batchRemove)批量操作的 结果。 |
| [SyncResult](arkts-assetstore-asset-syncresult-i.md) | 关键资产同步的结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Accessibility](arkts-assetstore-asset-accessibility-e.md) | 枚举，关键资产基于锁屏状态的访问控制类型。 |
| [AuthType](arkts-assetstore-asset-authtype-e.md) | 枚举，关键资产支持的用户认证类型。 |
| [ConflictResolution](arkts-assetstore-asset-conflictresolution-e.md) | 枚举，新增关键资产时的冲突（如：别名相同）处理策略。 |
| [ErrorCode](arkts-assetstore-asset-errorcode-e.md) | 表示错误码的枚举。 |
| [OperationType](arkts-assetstore-asset-operationtype-e.md) | 枚举，附属的操作类型。 |
| [ReturnType](arkts-assetstore-asset-returntype-e.md) | 枚举，关键资产查询返回的结果类型。 |
| [SyncType](arkts-assetstore-asset-synctype-e.md) | 枚举，关键资产支持的同步类型。 |
| [Tag](arkts-assetstore-asset-tag-e.md) | 枚举，关键资产支持的属性名称类型，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md#AssetMap)的键。 |
| [TagType](arkts-assetstore-asset-tagtype-e.md) | 枚举，关键资产属性支持的数据类型。 |
| [WrapType](arkts-assetstore-asset-wraptype-e.md) | 枚举，关键资产支持的加密导入导出类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthType](arkts-assetstore-asset-authtype-e-sys.md) | 枚举，关键资产支持的用户认证类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 关键资产属性的键-值对集合。 |
| [Value](arkts-assetstore-asset-value-t.md) | 关键资产属性的内容，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md#AssetMap)的值。 |

