# 清除PIN码认证状态(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

清除指定资源ID的PIN码认证状态。该接口用于在密钥操作完成后或需要重置认证状态时调用。

具体的场景介绍及规格，请参考[Ukey PIN码认证](huks-ukey-pin-authentication-management-overview.md)。

## 开发步骤

1. 获取资源ID。

2. 调用[clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate26)清除PIN码认证状态。

<!-- @[clear_pin_auth_state_ar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/ClearPinAuthState/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

// 资源ID
let resourceId: string = 'your_resource_id';

// 清除PIN码认证状态
async function clearUkeyPinAuthState(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.clearUkeyPinAuthState(resourceId);
    console.info('clearUkeyPinAuthState success');
  } catch (error) {
    console.error('clearUkeyPinAuthState failed: ' + JSON.stringify(error));
    throw error;
  }
}
```

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

// 清除PIN码认证状态
async function clearUkeyPinAuthState(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.clearUkeyPinAuthState(resourceId);
    console.info('clearUkeyPinAuthState success');
  } catch (error) {
    console.error('clearUkeyPinAuthState failed: ' + JSON.stringify(error));
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

// PIN码认证状态管理完整流程
async function pinAuthStateManagementExample(): Promise<void> {
  try {
    // 1. 打开资源
    await openResource(resourceId);
    
    // 2. 执行密钥操作（如签名等，可能需要PIN码认证）
    // ...
    
    // 3. 清除PIN码认证状态
    await clearUkeyPinAuthState(resourceId);
    
    // 4. 关闭资源
    await closeResource(resourceId);
    
    console.info('pinAuthStateManagementExample completed successfully');
  } catch (error) {
    console.error('pinAuthStateManagementExample failed: ' + JSON.stringify(error));
    // 出错时尝试关闭资源
    try {
      await closeResource(resourceId);
    } catch (e) {
      console.error('closeResource on error failed: ' + JSON.stringify(e));
    }
  }
}
```