# 获取资源ID(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在密钥管理扩展场景下，资源ID用于标识密钥管理扩展服务中的具体资源（如UKey设备、容器、密钥等）。从API版本26.0.0开始，应用可通过getResourceId获取资源ID，并使用该资源ID执行密钥生成与导入导出、通用查询、PIN码认证及清除PIN码认证状态等后续操作。

## 获取途径

执行具体的密钥管理扩展操作前需先获取resourceId，用于标识要操作的密钥管理扩展资源。resourceId长度为1-1024字节，可通过以下两种路径获取：

### 1. 证书管理服务获取

适用场景：浏览器双向SSL认证等需要用户选择证书的场景。

通过[openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)（由证书管理提供）展示证书列表，由用户选择证书。返回的[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)即为resourceId，每个证书链对应1个resourceId。

### 2. 通过getResourceId接口获取

适用场景：密钥生成、密钥导入等不需要证书选择的场景。从API版本26.0.0开始支持。

## 开发步骤

本文提供通过getResourceId接口获取resourceId的开发指导。

1. 传入提供者名称（providerName），建议包含厂商信息，全局唯一，长度最大为128字节。

2. 构造必选参数：
   - 通过[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入CryptoExtensionAbility名称。
   - 通过[HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入应用包名，包名长度为7-127。
   - 通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入厂商自定义的资源信息。

3. 调用[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid)获取resourceId。

## 开发案例
```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let providerName: string = 'testProviderName';
let abilityName: string = 'CryptoExtensionAbility1';
let bundleName: string = 'com.example.cryptoapplication';
// 资源信息，格式和内容由密钥管理扩展服务实现方定义
let resourceInfo: string = 'vendor_defined_resource_info';

function StringToUint8Array(str: string): Uint8Array {
  const encoder = new util.TextEncoder();
  return encoder.encodeInto(str);
}

async function getResourceId(): Promise<string> {
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: StringToUint8Array(abilityName),
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
      value: StringToUint8Array(bundleName),
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
      value: StringToUint8Array(resourceInfo),
    },
  ];

  try {
    const resourceId: string = await huksExternalCrypto.getResourceId(providerName, extProperties);
    console.info(`promise: getResourceId success, resourceId: ${resourceId}`);
    return resourceId;
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: getResourceId failed, errCode: ${e.code}, errMsg: ${e.message}`);
    throw error;
  }
}
```