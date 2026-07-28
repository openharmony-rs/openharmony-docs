# 公钥导出(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutitian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，在密钥管理扩展场景下（UKey物理设备、虚拟智能卡等），公钥导出能力支持从外部密钥管理服务中导出指定密钥的公钥。导出的公钥可用于证书申请、密钥协商等场景。

// 规格

具体的场景介绍请参考[密钥生成与导入导出介绍](huks-extension-key-generation-import-overview.md)。

## 开发步骤

1. 通过[2.1 获取资源ID](#21-获取资源id)获取resourceId，并通过[2.2 打开资源](#22-打开资源)。
2. 调用[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9)导出公钥，密钥参数中需指定[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示该密钥由外部密钥管理扩展管理。
3. 通过[2.3 关闭资源](#23-关闭资源)。

## 开发案例

```ts
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId);
    console.info('promise: openResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: openResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function exportPublicKey(keyAlias: string): Promise<Uint8Array> {
  let publicKey: Uint8Array = new Uint8Array();
  try {
    const exportProperties: Array<huks.HuksParam> = [
      {
        tag: huks.HuksTag.HUKS_TAG_KEY_CLASS,
        value: huks.HuksKeyClass.HUKS_KEY_CLASS_EXTENSION
      }
    ];
    const exportOptions: huks.HuksOptions = {
      properties: exportProperties
    };
    const data = await huks.exportKeyItem(keyAlias, exportOptions);
    publicKey = data.outData as Uint8Array;
    console.info('promise: exportKeyItem success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: exportKeyItem failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
  return publicKey;
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

async function extensionKeyExport(): Promise<Uint8Array> {
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
    const keyAlias = resourceId;  // keyAlias 即为 resourceId

    // 2. 打开资源
    await openResource(resourceId, []);

    // 3. 导出公钥
    const publicKey = await exportPublicKey(keyAlias);
    console.info(`promise: public key length: ${publicKey.length}`);

    // 4. 关闭资源
    await closeResource(resourceId);

    console.info('promise: extensionKeyExport completed successfully.');
    return publicKey;
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: extensionKeyExport failed, errCode: ${e.code}, errMsg: ${e.message}`);
    return new Uint8Array();
  }
}
```