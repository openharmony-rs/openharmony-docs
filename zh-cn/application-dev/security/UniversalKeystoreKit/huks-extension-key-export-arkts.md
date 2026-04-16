# 公钥导出(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutitian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在外部密钥管理扩展场景下，公钥导出能力支持从扩展设备导出指定密钥的公钥。导出的公钥可用于证书申请、密钥协商等场景。

具体的场景介绍及接口说明，请参考[密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)。

## 开发步骤

1. 获取外部密钥管理扩展的资源ID。具体请参考[获取外部密钥管理扩展资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)。

2. 打开资源，获取资源句柄。

3. 调用[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9)导出公钥。

4. 关闭资源。

## 开发案例

``` TypeScript
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';
// 密钥别名（待导出公钥的密钥）
let keyAlias: string = 'extension_key';

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

// 公钥导出完整流程
async function extensionKeyExport(): Promise<Uint8Array> {
  try {
    // 1. 打开资源
    await openResource(resourceId);
    
    // 2. 导出公钥
    let publicKey = await exportPublicKey(keyAlias);
    console.info('public key length: ' + publicKey.length);
    
    // 3. 关闭资源
    await closeResource(resourceId);
    
    console.info('extensionKeyExport completed successfully');
    return publicKey;
  } catch (error) {
    console.error('extensionKeyExport failed: ' + JSON.stringify(error));
    // 出错时尝试关闭资源
    try {
      await closeResource(resourceId);
    } catch (e) {
      console.error('closeResource on error failed: ' + JSON.stringify(e));
    }
    throw error;
  }
}
```