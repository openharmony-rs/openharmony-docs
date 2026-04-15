# 外部密钥管理扩展密钥生成(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在外部密钥管理扩展场景下，密钥生成能力支持在扩展设备内生成密钥对。密钥用途等参数传递给Extension后，由Extension实现方根据业务场景自行处理，HUKS不做额外校验。

具体的场景介绍及开发流程，请参考[外部密钥管理扩展密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)。

## 开发步骤

1. 获取外部密钥管理扩展的资源ID。具体请参考[获取外部密钥管理扩展资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)。

2. 打开资源，获取资源句柄。

3. 调用[generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9)生成密钥对。

4. 关闭资源。

## 公钥导出

密钥生成完成后，如需导出公钥用于证书申请等场景，可调用[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9)接口。具体请参考[公钥导出(ArkTS)](huks-extension-key-export-arkts.md)。

<!-- @[generate_key_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/ExtensionKeyGeneration/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';
// 密钥别名
let keyAlias: string = 'extension_key';

// 密钥生成参数
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
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN
  }
];

let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array([])
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

// 生成密钥
async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<void> {
  try {
    await huks.generateKeyItem(keyAlias, huksOptions);
    console.info('generateKeyItem success');
  } catch (error) {
    console.error('generateKeyItem failed: ' + JSON.stringify(error));
    throw error;
  }
}

// 导出公钥
async function exportPublicKey(keyAlias: string, huksOptions: huks.HuksOptions): Promise<Uint8Array> {
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

// 密钥生成完整流程
async function extensionKeyGeneration(): Promise<void> {
  try {
    // 1. 打开资源
    await openResource(resourceId);
    
    // 2. 生成密钥
    await generateKeyItem(keyAlias, huksOptions);
    
    // 3. 关闭资源
    await closeResource(resourceId);
    
    console.info('extensionKeyGeneration completed successfully');
  } catch (error) {
    console.error('extensionKeyGeneration failed: ' + JSON.stringify(error));
    // 出错时尝试关闭资源
    try {
      await closeResource(resourceId);
    } catch (e) {
      console.error('closeResource on error failed: ' + JSON.stringify(e));
    }
  }
}
```

## 错误码说明

密钥生成过程中可能返回的错误码：

| 错误码 | 说明 |
| -------- | -------- |
| 12000001 | 参数无效或丢失 |
| 12000002 | 算法参数无效或丢失 |
| 12000005 | IPC通信失败 |
| 12000011 | 查询实体不存在 |
| 12000012 | 设备环境或输入参数异常 |
| 12000014 | 内存不足 |
| 12000018 | 输入参数无效 |
| 12000020 | 提供者操作失败，扩展内部处理错误 |
| 12000024 | 提供者或UKey忙 |

更多错误码说明请参考[HUKS错误码](../../reference/apis-universal-keystore-kit/js-apis-huks.md#错误码)。

## 相关文档

- [外部密钥管理扩展密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)
- [获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)
- [密钥导入(ArkTS)](huks-extension-key-import-arkts.md)
- [资源管理](huks-resource-management-overview.md)