# 获取错误信息(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，huksExternalCrypto提供getErrorInfo接口，用于获取最近一次外部密钥操作的Extension错误信息。

## 功能说明

getErrorInfo接口仅返回Extension的错误信息：

- **errno != 0**：Extension返回的错误码
- **errno == 0**：Extension未返回错误信息，保持上一次的错误信息

HUKS内部错误通过异常抛出，不通过此接口获取。

## 开发步骤

1. 调用外部密钥操作接口（如authUkeyPin、getProperty等）。

2. 操作失败后，调用[getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo)获取Extension错误信息。

## 开发案例

### Extension返回错误场景

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function testExtensionError(): Promise<void> {
  const testResourceId = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: "testKey"
  });
  const params: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
  
  try {
    await huksExternalCrypto.authUkeyPin(testResourceId, params);
  } catch (error) {
    const errorInfo = huksExternalCrypto.getErrorInfo();
    if (errorInfo.errno !== 0) {
      console.info(`Extension error code: ${errorInfo.errno}`);
      console.info(`Extension error desc: ${errorInfo.errorDesc}`);
    }
  }
}
```

### 错误信息保持场景

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function testErrorInfoRetain(): Promise<void> {
  const resourceId1 = "resource_id_1";
  const resourceId2 = "resource_id_2";
  const params: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
  
  try {
    await huksExternalCrypto.authUkeyPin(resourceId1, params);
  } catch (error) {
    const errorInfo1 = huksExternalCrypto.getErrorInfo();
    console.info(`First error errno: ${errorInfo1.errno}`);
  }
  
  try {
    await huksExternalCrypto.authUkeyPin(resourceId2, params);
  } catch (error) {
    const errorInfo2 = huksExternalCrypto.getErrorInfo();
    if (errorInfo2.errno === 0) {
      console.info('Extension未返回错误信息，保持上次的错误');
    } else {
      console.info(`Extension error errno: ${errorInfo2.errno}`);
    }
  }
}
```

## 错误信息更新规则

| 场景 | errno | errorDesc |
| ---- | ----- | --------- |
| Extension返回错误信息结构体 | Extension错误码 | Extension描述 |
| Extension未返回错误信息结构体 | 0（保持上次） | 保持上次的描述 |
| 操作成功或HUKS内部错误 | 不更新，保持上次的错误信息 | 不更新，保持上次的错误信息 |

## 注意事项

1. 此接口仅返回Extension的错误信息，HUKS内部错误通过异常抛出显示。

2. Extension未返回错误信息结构体时（errno为0），保持上一次的错误信息。

3. 建议在操作失败后立即调用getErrorInfo获取Extension错误信息。

4. 错误信息覆盖范围：authUkeyPin、getUkeyPinAuthState、getProperty、setProperty、openResource、closeResource、clearUkeyPinAuthState、getResourceId等接口。