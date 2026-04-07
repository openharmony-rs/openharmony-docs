# 批量更新关键资产(ArkTS)

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @JeremyXu-->
<!--Designer: @skye_you-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 接口介绍

从版本26.0.0开始，系统提供异步接口[batchUpdate](../../reference/apis-asset-store-kit/js-apis-asset.md#assetbatchupdate)以便开发者批量更新关键资产。

在批量更新关键资产时，关键资产属性的内容（AssetMap）参数如下表所示：

>**注意：**
>
>下表中“ALIAS”和名称包含“DATA_LABEL”的关键资产属性，用于存储业务自定义信息，其内容不会被加密，请勿存放敏感个人数据。

- **sourceAttributes的参数列表：**

  | 属性名称（Tag）        | 属性内容（Value）                                             | 是否必选  | 说明                                             |
  | --------------------- | ------------------------------------------------------------ | -------- | ------------------------------------------------ |
  | ALIAS                 | 类型为Uint8Array，长度为1-256字节。                            | 必选     | 关键资产别名，每条关键资产的唯一索引。           |
  | ACCESSIBILITY         | 类型为number，取值范围详见[Accessibility](../../reference/apis-asset-store-kit/js-apis-asset.md#accessibility)。 | 可选     | 基于锁屏状态的访问控制。                                     |
  | REQUIRE_PASSWORD_SET  | 类型为boolean。                                                   | 可选     | 是否仅在设置了锁屏密码的情况下，可访问关键资产。为true时表示更新仅用户设置了锁屏密码才允许访问的关键资产；为false时表示更新无论用户是否设置锁屏密码，均可访问的关键资产。     |
  | AUTH_TYPE             | 类型为number，取值范围详见[AuthType](../../reference/apis-asset-store-kit/js-apis-asset.md#authtype)。 | 可选     | 访问关键资产所需的用户认证类型。                   |
  | SYNC_TYPE             | 类型为number，取值范围详见[SyncType](../../reference/apis-asset-store-kit/js-apis-asset.md#synctype)。 | 可选     | 关键资产支持的同步类型。                           |
  | IS_PERSISTENT         | 类型为boolean。                                                   | 可选     | 在应用卸载时是否需要保留关键资产。为true时表示更新应用卸载后会被保留的关键资产；为false时表示更新应用卸载后会被删除的关键资产。               |
  | DATA_LABEL_CRITICAL_1 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_2 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_3 | 类型为Uint8Array，长度为1-2048字节。                       | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_CRITICAL_4 | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且有完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_1   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_2   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_3   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_4   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | REQUIRE_ATTR_ENCRYPTED<sup>14+</sup> | 类型为boolean。 | 可选 | 是否更新业务自定义附属信息被加密的数据。为true时表示更新业务自定义附属信息加密存储的数据，为false时表示更新业务自定义附属信息不加密存储的数据。默认值为false。|
  | GROUP_ID<sup>18+</sup> | 类型为Uint8Array，长度为7-127字节。 | 可选 | 待更新的关键资产所属群组，默认更新不属于任何群组的关键资产。|

- **destAttributes的参数列表：**

  | 属性名称（Tag）        | 属性内容（Value）                      | 是否必选  | 说明                                                         |
  | --------------------- | -------------------------------| -------- | ------------------------------- |
  | SECRET                | 类型为Uint8Array，长度为1-1024字节。                           | 可选     | 关键资产明文。                                                 |
  | DATA_LABEL_NORMAL_1   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_2   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_3   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_4   | 类型为Uint8Array，长度为1-2048字节。                        | 可选     | 关键资产附属信息，内容由业务自定义且无完整性保护。<br/>**说明：** API12前长度为1-512字节。 |
  | DATA_LABEL_NORMAL_LOCAL_1<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_2<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_3<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |
  | DATA_LABEL_NORMAL_LOCAL_4<sup>12+</sup> | 类型为Uint8Array，长度为1-2048字节。 | 可选 | 关键资产附属的本地信息，内容由业务自定义且无完整性保护，该项信息不会进行同步。 |

## 约束和限制

批量更新的关键资产必须具有相同的[GROUP_ID](../../reference/apis-asset-store-kit/js-apis-asset.md#tag)和[REQUIRE_ATTR_ENCRYPTED](../../reference/apis-asset-store-kit/js-apis-asset.md#tag)属性。

批量更新的关键资产数量最大值为100。

## 开发步骤

> **说明：**
>
> 以下为批量更新接口的使用示例。
>
> 在更新前，需确保已有关键资产，可参考[指南文档](asset-js-add.md)新增关键资产，否则将抛出NOT_FOUND错误（错误码24000002）。

批量更新两条关键资产，将别名分别为demo_alias1和demo_alias2的关键资产明文更新为demo_pwd_new1和demo_pwd_new2。

1. 引用头文件，定义工具函数。
   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/batch_operation.ets) -->
   
   ``` TypeScript
   import { asset } from '@kit.AssetStoreKit';
   import { util } from '@kit.ArkTS';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   function stringToArray(str: string): Uint8Array {
     let textEncoder = new util.TextEncoder();
     return textEncoder.encodeInto(str);
   }
   ```

2. 参考如下示例代码，进行业务功能开发。
   <!-- @[batch_update](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/batch_operation.ets) -->
   
   ``` TypeScript
   let srcAttrs: asset.AssetMap[] = [];
   let srcAttr1: asset.AssetMap = new Map();
   srcAttr1.set(asset.Tag.ALIAS, stringToArray('demo_alias1'));
   srcAttrs.push(srcAttr1);
   let srcAttr2: asset.AssetMap = new Map();
   srcAttr2.set(asset.Tag.ALIAS, stringToArray('demo_alias2'));
   srcAttrs.push(srcAttr2);
   
   let destAttrs: asset.AssetMap[] = [];
   let destAttr1: asset.AssetMap = new Map();
   destAttr1.set(asset.Tag.SECRET, stringToArray('demo_pwd_new1'));
   destAttrs.push(destAttr1);
   let destAttr2: asset.AssetMap = new Map();
   destAttr2.set(asset.Tag.SECRET, stringToArray('demo_pwd_new2'));
   destAttrs.push(destAttr2);
   
   try {
     asset.batchUpdate(srcAttrs, destAttrs).then((res: asset.BatchResult) => {
       console.info(`Succeeded in batch updating Asset, failedCount: ${res.failedCount}`);
       if (res.failedCount > 0) {
         for (let i = 0; i < res.failedErrorInfos.length; i++) {
           console.error(`Failed to update Asset at index ${res.failedErrorInfos[i].index},
             errCode: ${res.failedErrorInfos[i].errCode}, message: ${res.failedErrorInfos[i].message}`);
         }
       }
     }).catch((err: BusinessError) => {
       console.error(`Failed to batch update Asset. Code is ${err.code}, message is ${err.message}`);
     })
   } catch (error) {
     let err = error as BusinessError;
     console.error(`Failed to batch update Asset. Code is ${err.code}, message is ${err.message}`);
   }
   ```