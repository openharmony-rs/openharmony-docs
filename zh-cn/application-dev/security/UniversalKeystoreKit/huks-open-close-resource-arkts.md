# 打开资源/关闭资源(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

应用在密钥操作之前（密钥操作、通用操作、PIN码认证等），需要先打开资源。操作完成后需要关闭资源，避免资源泄漏。

具体的场景介绍及规格，请参考[资源管理介绍及规格](huks-resource-management-overview.md)。

## 打开资源

### 开发步骤

1. 获取资源ID。可通过[证书选择接口](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取，或通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。

2. 调用[openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource26)打开资源。

<!-- @[open_resource_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/OpenCloseResource/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';

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
```

### 错误码说明

打开资源过程中可能返回的错误码：

| 错误码 | 说明 |
| -------- | -------- |
| 12000005 | IPC通信失败 |
| 12000006 | UKey驱动操作失败 |
| 12000011 | 查询实体不存在 |
| 12000012 | 设备环境或输入参数异常 |
| 12000014 | 内存不足 |
| 12000018 | 输入参数无效 |
| 12000020 | 提供者操作失败 |
| 12000024 | 提供者或UKey忙 |

更多错误码说明请参考[huksExternalCrypto错误码](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#错误码)。

## 关闭资源

### 开发步骤

1. 获取资源ID。

2. 调用[closeResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptocloseresource26)关闭资源。该接口会清理该资源关联的PIN认证状态和会话handle。

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';

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
```

### 错误码说明

关闭资源过程中可能返回的错误码：

| 错误码 | 说明 |
| -------- | -------- |
| 12000005 | IPC通信失败 |
| 12000006 | UKey驱动操作失败 |
| 12000011 | 查询实体不存在 |
| 12000012 | 设备环境或输入参数异常 |
| 12000014 | 内存不足 |
| 12000018 | 输入参数无效 |
| 12000020 | 提供者操作失败 |
| 12000024 | 提供者或UKey忙 |

更多错误码说明请参考[huksExternalCrypto错误码](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#错误码)。

## 完整示例

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';

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

// 资源管理完整流程
async function resourceManagementExample(): Promise<void> {
  try {
    // 1. 打开资源
    await openResource(resourceId);
    
    // 2. 执行密钥操作（如签名、加密等）
    // ...
    
    // 3. 关闭资源
    await closeResource(resourceId);
    
    console.info('resourceManagementExample completed successfully');
  } catch (error) {
    console.error('resourceManagementExample failed: ' + JSON.stringify(error));
    // 出错时尝试关闭资源
    try {
      await closeResource(resourceId);
    } catch (e) {
      console.error('closeResource on error failed: ' + JSON.stringify(e));
    }
  }
}
```

## 相关文档

- [资源管理介绍及规格](huks-resource-management-overview.md)
- [打开资源/关闭资源(C/C++)](huks-open-close-resource-ndk.md)
- [获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)