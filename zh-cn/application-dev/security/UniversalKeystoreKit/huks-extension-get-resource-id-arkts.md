# 获取外部密钥管理扩展资源ID(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在外部密钥管理扩展场景下，获取资源ID是密钥操作的第一步。资源ID用于标识外部密钥管理扩展的具体资源（如UKey设备、容器、密钥等），后续的密钥生成、导入、导出等操作都需要使用资源ID。

## 开发步骤

1. 准备提供者名称（providerName），该名称需要全局唯一，建议包含厂商信息。

2. 构造资源信息参数，通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag26)携带资源信息。

3. 调用[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取资源ID。

<!-- @[get_resource_id_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/ExtensionGetResourceId/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 提供者名称，需要全局唯一，建议包含厂商信息
let providerName: string = 'vendor_ukey_provider';

// 构造资源信息
// 资源信息格式和内容由厂商自定义，例如包含UKey设备名、应用名、容器名等
function buildResourceInfo(): Uint8Array {
  // 示例：构造JSON格式的资源信息
  let resourceInfo = {
    deviceName: 'ukey_device_001',
    appName: 'banking_app',
    containerName: 'sign_container',
    keyId: 'key_001'
  };
  
  let jsonString = JSON.stringify(resourceInfo);
  let encoder = new TextEncoder();
  return encoder.encode(jsonString);
}

// 获取资源ID
async function getResourceId(providerName: string, resourceInfo: Uint8Array): Promise<string> {
  // 构造参数
  let params: huksExternalCrypto.HuksExternalCryptoParam[] = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
      value: resourceInfo
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
    // 1. 构造资源信息
    let resourceInfo = buildResourceInfo();
    
    // 2. 获取资源ID
    let resourceId = await getResourceId(providerName, resourceInfo);
    
    console.info('extensionGetResourceIdExample completed successfully');
    return resourceId;
  } catch (error) {
    console.error('extensionGetResourceIdExample failed: ' + JSON.stringify(error));
    throw error;
  }
}
```

## 资源信息格式说明

> **说明：**
>
> 资源信息（resourceInfo）的格式和内容由Extension实现方定义。应用需要根据Extension厂商提供的说明构造相应的资源信息。

常见的资源信息字段可能包括：

| 字段名 | 说明 | 是否必选 |
| -------- | -------- | -------- |
| deviceName | UKey设备名称 | 由厂商定义 |
| appName | UKey应用名称 | 由厂商定义 |
| containerName | UKey容器名称 | 由厂商定义 |
| keyId | 密钥标识 | 由厂商定义 |

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

- [外部密钥管理扩展密钥生成与导入介绍](huks-extension-key-generation-import-overview.md)
- [密钥生成(ArkTS)](huks-extension-key-generation-arkts.md)
- [密钥导入(ArkTS)](huks-extension-key-import-arkts.md)
- [资源管理](huks-resource-management-overview.md)