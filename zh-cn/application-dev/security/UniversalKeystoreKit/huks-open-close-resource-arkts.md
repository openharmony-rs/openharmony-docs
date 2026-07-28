# 打开资源/关闭资源(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，huksExternalCrypto提供打开/关闭资源功能的ArkTS接口。

## 打开资源

应用在密钥操作之前（如密钥操作、签名/验签、PIN码认证等），需要先获取密钥管理扩展的资源ID，可参考[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)进行开发。

### 开发步骤

1. 通过[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)，得到resourceId。

2. 调用[openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource)打开资源。

### 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

const resourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

async function openResource(): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId, []);
    console.info('promise: openResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: openResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## 关闭资源

执行完所有密钥管理扩展操作后必须手动关闭已打开的资源，避免资源泄漏。

### 开发步骤

1. 通过[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)，得到resourceId。

2. 调用[closeResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptocloseresource)关闭资源。

### 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

const resourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: { key: "testKey" } as ESObject,
});

async function closeResource(): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId, []);
    console.info('promise: closeResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: closeResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```