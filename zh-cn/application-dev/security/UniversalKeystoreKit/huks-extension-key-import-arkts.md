# 密钥导入(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutitian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，在密钥管理扩展场景下（UKey物理设备、虚拟智能卡等），HUKS支持将加密封装的密钥对导入到密钥管理扩展服务中。密钥用途等参数由外部密钥管理服务提供方根据业务场景自行处理，HUKS不做额外校验。

具体的场景介绍请参考[密钥生成与导入导出介绍](huks-extension-key-generation-import-overview.md)。

// TODO：规格，这个接口的两个resourceId必须都在里面打开过，这个规格要写清楚

## 开发步骤

// TODO
1. 通过[2.1 获取资源ID](#21-获取资源id)获取resourceId，并通过[2.2 打开资源](#22-打开资源)。

2. 调用[importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportwrappedkeyitem9)导入加密封装的密钥对。密钥参数中需指定[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示该密钥由密钥管理扩展服务管理。

3. 通过[2.3 关闭资源](#23-关闭资源)。

## 开发案例

```ts
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

function StringToUint8Array(str: string): Uint8Array {
  const encoder = new util.TextEncoder();
  return encoder.encodeInto(str);
}

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId);
    console.info('promise: openResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: openResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function importWrappedKeyItem(keyAlias: string, wrappingKeyAlias: string, huksOptions: huks.HuksOptions): Promise<void> {
  try {
    await huks.importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions);
    console.info('promise: importWrappedKeyItem success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: importWrappedKeyItem failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId);
    console.info('promise: closeResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: closeResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function extensionKeyImport(): Promise<void> {
  try {
    // 1. 获取 resourceId
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        value: StringToUint8Array("CryptoExtensionAbility1"),
      },
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
        value: StringToUint8Array("com.example.cryptoapplication"),
      },
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
        value: StringToUint8Array("vendor_defined_resource_info"),
      },
    ];
    const resourceId: string = await huksExternalCrypto.getResourceId(providerName, extProperties);
    const keyAlias = resourceId;
    const wrappingKeyAlias = resourceId;

    // 2. 构造密钥参数
    const properties: Array<huks.HuksParam> = [
      { tag: huks.HuksTag.HUKS_TAG_KEY_CLASS, value: huks.HuksKeyClass.HUKS_KEY_CLASS_EXTENSION },
      { tag: huks.HuksTag.HUKS_TAG_ALGORITHM, value: huks.HuksKeyAlg.HUKS_ALG_RSA },
      { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048 },
      { tag: huks.HuksTag.HUKS_TAG_PURPOSE, value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT }
    ];
    // 加密封装的密钥数据（由外部密钥管理服务提供方定义格式）
    const wrappedKeyData: Uint8Array = new Uint8Array([/* 封装密钥数据 */]);
    const huksOptions: huks.HuksOptions = {
      properties: properties,
      inData: wrappedKeyData
    };

    // 3. 打开资源
    await huksExternalCrypto.openResource(resourceId, []);

    // 4. 导入加密封装的密钥
    await huks.importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions);

    // 5. 关闭资源
    await huksExternalCrypto.closeResource(resourceId, []);

    console.info('promise: extensionKeyImport completed successfully.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: extensionKeyImport failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```