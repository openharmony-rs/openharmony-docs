# 查询(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本22开始，huksExternalCrypto提供查询[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)接口。

## 规格说明

打开密钥管理扩展服务中的资源后，可调用该接口获取属性信息，由密钥管理扩展服务（即[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)）实现方提供具体的propertyId。具体的场景介绍请参考[获取属性介绍及规格](huks-ukey-general-query-overview.md)。// TODO

- resourceId为已通过[打开资源](huks-open-close-resource-arkts.md#打开资源)步骤打开的资源ID，长度为1-1024字节。

- propertyId需要与密钥管理扩展约定调用规则，长度为1-100字节。建议采用GM/T 0016-2023标准中定义的SKF函数名称。

- 输出参数通过[HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)携带，应用可以提取查询的属性数据，并按照和密钥管理扩展服务实现方的约定，解析数据。

> **PIN认证说明**：是否需要PIN认证取决于propertyId和密钥管理扩展的实现。查询设备信息等操作通常不需要，涉及密钥属性或敏感信息时，通常需要先完成PIN认证。

## 开发步骤

1. 通过[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)获取resourceId，并传入该resourceId[打开资源](huks-open-close-resource-arkts.md#打开资源)。

2. 构造propertyId和可选输入参数。

3. 调用[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)获取属性信息。

## 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getDeviceInfo(): Promise<void> {
  // 假设已通过 openResource 打开了 resourceId
  const testResourceId = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: { key: "testKey" } as ESObject
  });

  // 设置propertyId
  const propertyId = "SKF_GetDevInfo";
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

  // 调用getProperty获取属性信息
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ${JSON.stringify(data)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: getProperty input arg invalid.');
  }
}
```

