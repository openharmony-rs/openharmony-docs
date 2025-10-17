# 查询需要用户认证的关键资产(ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 接口介绍

可通过API文档查看此功能的相关接口：

| 异步接口 | 同步接口 | 说明 |
| ----- | ------ | ------- |
| [preQuery(query: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetprequery) | [preQuerySync(query: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetprequerysync12) | 查询预处理。|
| [query(query: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetquery) | [querySync(query: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetquerysync12) | 查询关键资产。|
| [postQuery(handle: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetpostquery) | [postQuerySync(handle: AssetMap)](../../reference/apis-asset-store-kit/js-apis-asset.md#assetpostquerysync12) | 查询后置处理。 |

查询需要用户认证的关键资产时，关键资产属性的内容（AssetMap）参数如下表所示：

>**注意：**
>
>下表中“ALIAS”和名称包含“DATA_LABEL”的关键资产属性，用于存储业务自定义信息，其内容不会被加密，请勿存放敏感个人数据。

- **preQuery参数列表**

  | 属性名称（Tag）        | 属性内容（Value）           | 是否必选  | 说明                  |
  | --------------------- | ---------------------------| -------- | -------------------------- |
  | ALIAS                 | 类型为Uint8Array，长度为1-256字节。                            | 可选     | 关键资产别名，每条关键资产的唯一索引。          |
  | ACCESSIBILITY         | 类型为number，取值范围详见[Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)。 | 可选     | 基于锁屏状态的访问控制。                                     |
  | REQUIRE_PASSWORD_SET  | 类型为boolean。                                                   | 可选     | 是否仅在设置了锁屏密码的情况下，可访问关键资产。为true时表示查询仅用户设置了锁屏密码才允许访问的关键资产；为false时表示查询无论用户是否设置锁屏密码，均可访问的关键资产。     |
  | AUTH_TYPE             | 类型为number，取值范围详见[AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)。 | 可选     | 访问关键资产所需的用户认证类型。                  |
  | AUTH_VALIDITY_PERIOD  | 类型为number，取值范围：1-600，单位为秒。        | 可选     | 用户认证的有效期，默认值为60。          |
  | SYNC_TYPE             | 类型为number，取值范围详见[SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)。 | 可选     | 关键资产支持的同步类型。                           |
  | IS_PERSISTENT         | 类型为boolean。                                                   | 可选     | 在应用卸载时是否需要保留关键资产。为true时表示查询应用卸载后会被保留的关键资产；为false时表示查询应用卸载后会被删除的关键资产。               |
  | DATA_LABEL_CRITICAL_1 | 类型为Uint8Array，长度为1-2048字节。                       | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_2 | 类型为Uint8Array，长度为1-2048字节。                      | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_3 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_4 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_1   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_2   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_3   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_4   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | 类型为boolean。 | 可选 | 是否查询业务自定义附属信息被加密的数据。为true时表示查询业务自定义附属信息加密存储的数据，为false时表示查询业务自定义附属信息不加密存储的数据。默认值为false。|
  | GROUP_ID<sup>18+</sup> | 类型为Uint8Array，长度为7-127字节。 | 可选 | 待查询的关键资产所属群组，默认查询不属于任何群组的关键资产。|

- **query参数列表**

  | 属性名称（Tag）        | 属性内容（Value）                                             | 是否必选  | 说明                                             |
  | --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
  | ALIAS                 | 类型为Uint8Array，长度为1-256字节。                            | 必选     | 关键资产别名，每条关键资产的唯一索引。       |
  | AUTH_CHALLENGE        | 类型为Uint8Array，长度为32字节。                               | 必选     | 用户认证的挑战值。                              |
  | AUTH_TOKEN            | 类型为Uint8Array。<br>API 20开始：长度为1-1024字节。<br>API 11-19：长度为148字节。       | 必选     | 用户认证通过的授权令牌。                         |
  | RETURN_TYPE           | 类型为number，asset.ReturnType.ALL。                           | 必选     | 关键资产查询返回的结果类型。                    |
  | ACCESSIBILITY         | 类型为number，取值范围详见[Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)。 | 可选     | 基于锁屏状态的访问控制。                                     |
  | REQUIRE_PASSWORD_SET  | 类型为boolean。                                                   | 可选     | 是否仅在设置了锁屏密码的情况下，可访问关键资产。为true时表示查询仅用户设置了锁屏密码才允许访问的关键资产；为false时表示查询无论用户是否设置锁屏密码，均可访问的关键资产。     |
  | AUTH_TYPE             | 类型为number，取值范围详见[AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)。 | 可选     | 访问关键资产所需的用户认证类型。                  |
  | SYNC_TYPE             | 类型为number，取值范围详见[SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)。 | 可选     | 关键资产支持的同步类型。                           |
  | IS_PERSISTENT         | 类型为boolean。                                                   | 可选     | 在应用卸载时是否需要保留关键资产。为true时表示查询应用卸载后会被保留的关键资产；为false时表示查询应用卸载后会被删除的关键资产。     |
  | DATA_LABEL_CRITICAL_1 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_2 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_3 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_4 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_1   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_2   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_3   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_4   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | 类型为boolean。 | 可选 | 是否查询业务自定义附属信息被加密的数据。为true时表示查询业务自定义附属信息加密存储的数据，为false时表示查询业务自定义附属信息不加密存储的数据。默认值为false。|
  | GROUP_ID<sup>18+</sup> | 类型为Uint8Array，长度为7-127字节。 | 可选 | 待查询的关键资产所属群组，默认查询不属于任何群组的关键资产。|

- **postQuery参数列表**

  | 属性名称（Tag）      | 属性内容（Value）               | 是否必选  | 说明                 |
  | ------------------- | ------------------------------ | -------- | -------------------- |
  | AUTH_CHALLENGE      | 类型为Uint8Array，长度为32字节。 | 必选     | 用户认证的挑战值。 |
  | GROUP_ID<sup>18+</sup> | 类型为Uint8Array，长度为7-127字节。 | 可选 | 待清理关键资产所属群组，默认清理内存中不属于任何群组的关键资产。|

## 代码示例

> **说明：**
>
> 本模块提供了异步和同步两套接口，以下为异步接口的使用示例，同步接口详见[API文档](../../reference/apis-asset-store-kit/js-apis-asset.md)。

查询别名是demo_alias且需要用户认证的关键资产。示例中引入的@ohos.userIAM.userAuth用法详见[userAuth文档](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#start10)。

<!-- @[query_user_auth_asset](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/query_auth.ets) -->
