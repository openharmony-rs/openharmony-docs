# 打开资源/关闭资源(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## 打开资源

从API版本26.0.0开始，huksExternalCrypto提供打开/关闭资源功能的ArkTs接口。应用在密钥操作之前（密钥操作、通用操作、PIN码认证等），需要先调用[openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource26)打开资源。打开资源需要获取resourceId，resourceId可通过[证书选择接口](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取，或通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。

### 开发步骤

1. 通过[证书选择接口](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取keyUri作为resourceId，或通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。

2. 调用[openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource26)打开资源。

### 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function openResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId)
      .then(() => {
        console.info(`promise: openResource success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: openResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: openResource input arg invalid`);
  }
}
```

## 关闭资源

生态应用调用证书HAP界面，展示证书列表，用户选择证书，生态应用拿到对应的resourceId，关闭资源依赖于对应的resourceId。具体的场景介绍及规格，请参考[资源管理介绍及规格](huks-resource-management-overview.md)。

### 开发步骤

1. 通过[证书选择接口](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId，或通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。

2. 调用[closeResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptocloseresource26)关闭资源。该接口会回调[onClearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonclearukeypinauthstate)清理该资源关联的PIN认证状态，以及会回调[onFinishSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonfinishsession)清理该资源关联的会话handle。

### 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function closeResource(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId)
      .then(() => {
        console.info(`promise: closeResource success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: closeResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: closeResource input arg invalid`);
  }
}
```