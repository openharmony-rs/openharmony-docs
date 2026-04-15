# 获取资源ID(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在外部密钥管理扩展场景下，获取资源ID是操作的第一步。资源ID用于标识外部密钥管理扩展的具体资源（如UKey设备、容器、密钥等），后续的密钥生成、导入、导出、通用查询、PIN认证等操作都需要使用资源ID。

## 开发步骤

1. 准备提供者名称（providerName），该名称需要全局唯一，建议包含厂商信息。

2. 构造必选参数：通过[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入CryptoExtensionAbility名称，通过[HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入Bundle名称。

3. （可选）通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag26)携带厂商自定义的资源信息。

4. 调用[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取资源ID。

<!-- @[get_resource_id_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/ExtensionGetResourceId/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 提供者名称，需要全局唯一，建议包含厂商信息
let providerName: string = 'vendor_ukey_provider';
// Ability名称
let abilityName: string = 'CryptoExtension';
// Bundle名称
let bundleName: string = 'com.example.ukeyapp';

// 字符串转Uint8Array
function stringToUint8Array(str: string): Uint8Array {
  let encoder = new TextEncoder();
  return encoder.encode(str);
}

// 获取资源ID
async function getResourceId(
  providerName: string,
  abilityName: string,
  bundleName: string
): Promise<string> {
  // 构造必选参数：providerName、abilityName、bundleName
  let params: huksExternalCrypto.HuksExternalCryptoParam[] = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName)
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
      value: stringToUint8Array(bundleName)
    }
  ];
  
  try {
    let resourceId = await huksExternalCrypto.getResourceId(providerName, params);
    console.info('getResourceId success, resourceId: ' + resourceId);
    return resourceId;
  } catch (error) {
    console.error('getResourceId failed: ' + JSON.stringify(error));
    throw error;
  }
}

// 完整示例
async function extensionGetResourceIdExample(): Promise<string> {
  try {
    // 获取资源ID
    let resourceId = await getResourceId(providerName, abilityName, bundleName);
    
    console.info('extensionGetResourceIdExample completed successfully');
    return resourceId;
  } catch (error) {
    console.error('extensionGetResourceIdExample failed: ' + JSON.stringify(error));
    throw error;
  }
}
```

## 参数说明

获取资源ID时，需要传入以下参数：

| 参数 | 传入方式 | 说明 | 是否必选 |
| -------- | -------- | -------- | -------- |
| providerName | getResourceId第一个参数 | 提供者名称，全局唯一 | 必选 |
| abilityName | params中HUKS_EXT_CRYPTO_TAG_ABILITY_NAME | CryptoExtensionAbility名称 | 必选 |
| bundleName | params中HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME | 应用Bundle名称 | 必选 |
| resourceInfo | params中HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO | 厂商自定义资源信息 | 可选 |

> **说明：**
>
> 如果Extension实现方需要额外的资源信息（如UKey设备名、容器名等），可通过HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO传入。具体格式由厂商定义，请参考Extension厂商提供的说明。

## 错误码说明

获取资源ID过程中可能返回的错误码：

| 错误码 | 说明 |
| -------- | -------- |
| 12000002 | ability名称或bundle名称参数丢失 |
| 12000005 | IPC通信失败 |
| 12000011 | 提供者不存在 |
| 12000012 | 设备环境或输入参数异常 |
| 12000014 | 内存不足 |
| 12000018 | 输入参数无效 |
| 12000020 | 提供者操作失败，扩展内部处理错误 |
| 12000024 | 提供者或UKey忙 |

更多错误码说明请参考[huksExternalCrypto错误码](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#错误码)。

## 相关文档

- [密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)
- [密钥生成(ArkTS)](huks-extension-key-generation-arkts.md)
- [密钥导入(ArkTS)](huks-extension-key-import-arkts.md)
- [资源管理介绍及规格](huks-resource-management-overview.md)