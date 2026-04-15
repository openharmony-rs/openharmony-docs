# 密钥导入(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutitian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在外部密钥管理扩展场景下，密钥导入能力支持将加密封装的密钥对导入到扩展设备中。密钥用途等参数传递给Extension后，由Extension实现方根据业务场景自行处理，HUKS不做额外校验。

具体的场景介绍及开发流程，请参考[密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)。

## 开发步骤

1. 获取外部密钥管理扩展的资源ID。具体请参考[获取外部密钥管理扩展资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)。

2. 打开资源，获取资源句柄。

3. 获取或生成用于解封密钥的密钥句柄（wrappedHandle）。

4. 调用[importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportwrappedkeyitem9)导入加密封装的密钥对。

5. 关闭资源。

## 公钥导出

密钥导入完成后，如需导出公钥用于证书申请等场景，可调用[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9)接口。具体请参考[公钥导出(ArkTS)](huks-extension-key-export-arkts.md)。

<!-- @[import_key_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/ExtensionKeyImport/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';
// 密钥别名（导入后的密钥）
let keyAlias: string = 'extension_imported_key';
// 解封密钥别名（用于解封导入的密钥）
let wrappingKeyAlias: string = 'extension_wrapping_key';

// 密钥导入参数
let properties: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }
];

// 加密封装的密钥数据（由Extension实现方定义格式）
let wrappedKeyData: Uint8Array = new Uint8Array([/* 封装密钥数据 */]);

let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: wrappedKeyData
};

// 打开资源
async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId);
    console.info('openResource success');
  } catch (error) {
    console.error('openResource failed: ' + JSON.stringify(error));
    throw error;
  }
}

// 导入加密封装的密钥
async function importWrappedKeyItem(
  keyAlias: string,
  wrappingKeyAlias: string,
  huksOptions: huks.HuksOptions
): Promise<void> {
  try {
    await huks.importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions);
    console.info('importWrappedKeyItem success');
  } catch (error) {
    console.error('importWrappedKeyItem failed: ' + JSON.stringify(error));
    throw error;
  }
}

// 导出公钥
async function exportPublicKey(keyAlias: string): Promise<Uint8Array> {
  try {
    let exportOptions: huks.HuksOptions = {
      properties: [],
      inData: new Uint8Array([])
    };
    let data = await huks.exportKeyItem(keyAlias, exportOptions);
    console.info('exportKeyItem success');
    return data.outData as Uint8Array;
  } catch (error) {
    console.error('exportKeyItem failed: ' + JSON.stringify(error));
    throw error;
  }
}

// 关闭资源
async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId);
    console.info('closeResource success');
  } catch (error) {
    console.error('closeResource failed: ' + JSON.stringify(error));
    throw error;
  }
}

// 密钥导入完整流程
async function extensionKeyImport(): Promise<void> {
  try {
    // 1. 打开资源
    await openResource(resourceId);
    
    // 2. 导入加密封装的密钥
    // 注意：wrappingKeyAlias需要事先存在或通过generateKeyItem生成
    await importWrappedKeyItem(keyAlias, wrappingKeyAlias, huksOptions);
    
    // 3. 关闭资源
    await closeResource(resourceId);
    
    console.info('extensionKeyImport completed successfully');
  } catch (error) {
    console.error('extensionKeyImport failed: ' + JSON.stringify(error));
    // 出错时尝试关闭资源
    try {
      await closeResource(resourceId);
    } catch (e) {
      console.error('closeResource on error failed: ' + JSON.stringify(e));
    }
  }
}
```

## 密钥封装格式说明

> **说明：**
>
> 加密封装的密钥数据（wrappedKeyData）格式由Extension实现方定义。应用需要根据Extension厂商提供的说明准备相应的密钥封装数据。