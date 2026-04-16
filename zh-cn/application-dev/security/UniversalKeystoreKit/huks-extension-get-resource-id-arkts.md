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
   - 通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入厂商自定义的资源信息。

3. 调用[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取资源ID。

## 开发案例

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 提供者名称，建议包含厂商信息，全局唯一，长度最大为128字节
let providerName: string = 'testProviderName';
// Ability名称
let abilityName: string = 'CryptoExtension';
// Bundle名称
let bundleName: string = 'com.example.cryptoapplication';
// 资源信息，格式和内容由厂商自定义
let resourceInfo: string = 'vendor_defined_resource_info';

// 字符串转Uint8Array
function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
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
      value: StringToUint8Array(abilityName)
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
      value: StringToUint8Array(bundleName)
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
      value: StringToUint8Array(resourceInfo)
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
```