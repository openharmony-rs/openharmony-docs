# 获取资源ID(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在外部密钥管理扩展场景下，获取资源ID是操作的第一步。资源ID用于标识外部密钥管理扩展的具体资源（如UKey设备、容器、密钥等），后续的密钥生成、导入、导出、通用查询、PIN认证等操作都需要使用资源ID。

## 开发步骤

1. 准备提供者名称（providerName），建议包含厂商信息，全局唯一。长度最大为128字节。

2. 构造必选参数：
   - 通过[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入CryptoExtensionAbility名称。
   - 通过[HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入Bundle名称。
   - 通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag26)传入厂商自定义的资源信息。

3. 调用[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取资源ID。

<!-- @[get_resource_id_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/ExtensionGetResourceId/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 提供者名称，建议包含厂商信息，全局唯一，长度最大为128字节
let providerName: string = 'testProvider';
// Ability名称
let abilityName: string = 'CryptoExtension';
// Bundle名称
let bundleName: string = 'com.example.ukeyapp';
// 资源信息，格式和内容由厂商自定义
let resourceInfo: string = 'vendor_defined_resource_info';

// 字符串转Uint8Array
function stringToUint8Array(str: string): Uint8Array {
  let encoder = new TextEncoder();
  return encoder.encode(str);
}

// 获取资源ID
async function getResourceId(
  providerName: string,
  abilityName: string,
  bundleName: string,
  resourceInfo: string
): Promise<string> {
  // 构造必选参数
  let params: huksExternalCrypto.HuksExternalCryptoParam[] = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName)
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
      value: stringToUint8Array(bundleName)
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
      value: stringToUint8Array(resourceInfo)
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

async function extensionGetResourceIdExample(): Promise<string> {
  try {
    // 获取资源ID
    let resourceId = await getResourceId(providerName, abilityName, bundleName, resourceInfo);
    
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
| providerName | getResourceId第一个参数 | 提供者名称，建议包含厂商信息，全局唯一，长度最大为128字节 | 必选 |
| abilityName | params中HUKS_EXT_CRYPTO_TAG_ABILITY_NAME | CryptoExtensionAbility名称 | 必选 |
| bundleName | params中HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME | 应用Bundle名称 | 必选 |
| resourceInfo | params中HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO | 厂商自定义资源信息，格式和内容由厂商定义 | 必选 |

> **说明：**
>
> 资源信息（resourceInfo）的格式和内容由Extension实现方定义。应用需要根据Extension厂商提供的说明构造相应的资源信息。