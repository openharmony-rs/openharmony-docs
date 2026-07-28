# PIN码认证(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->


### 3.4 导出公钥（getProperty, SKF_ExportPublicKey）

在 PIN 认证流程中，调用方需要先获取 UKey 设备的公钥用于加密用户输入的 PIN 码。`getProperty` 接口在传入 `SKF_ExportPublicKey` 作为 propertyId 时，用于此用途。

**典型调用流程**：

```
  调用方                                HUKS 框架                      UKey 设备
   │                                       │                              │
   │ getProperty(resourceId,              │                              │
   │   'SKF_ExportPublicKey')             │                              │
   ├──────────────────────────────────────►│                              │
   │                                       │ 调用 UKey 设备内部接口            │
   │                                       ├─────────────────────────────►│
   │                                       │◄─────────────────────────────┤
   │                                       │  返回公钥 JSON                  │
   │◄───────────────────────────────────────┤                              │
   │ { publicKey, algo,                   │                              │
   │   transformation, size }             │                              │
   │                                       │                              │
   │ 用公钥加密用户输入的 PIN               │                              │
   │                                       │                              │
   │ authUkeyPin(resourceId, encryptedPin) │                              │
   ├──────────────────────────────────────►│                              │
```

**返回值说明**：`getProperty` 返回 `Array<HuksExternalCryptoParam>`，属性数据放在 `HUKS_EXT_CRYPTO_TAG_EXTRA_DATA` 标签中，内容为 JSON 字符串，包含以下 4 个字段：

| 字段 | 含义 |
|------|------|
| `publicKey` | 公钥数据（Uint8Array 的 Array 形式） |
| `algo` | 算法类型及密钥长度，如 `RSA1024` |
| `transformation` | 密码学操作参数（算法\|填充模式），如 `RSA1024\|PKCS1` |
| `size` | 公钥数据长度 |

调用方无需关心 `getProperty` 在 UKey 设备内部的实现方式，只需按下列步骤调用：

1. 调用 `getProperty` 传入 `propertyId='SKF_ExportPublicKey'` 获取公钥
2. 解析返回的 JSON，提取公钥数据
3. 使用提取出的公钥加密用户输入的 PIN 码
4. 调用 [authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoauthukeypin) 传入加密后的 PIN
从API 22开始，huksExternalCrypto提供PIN码认证功能接口。生态应用调用证书HAP界面，展示证书列表，用户选择证书后，浏览器根据选择的证书获取到resourceId，然后[打开资源](huks-open-close-resource-ndk.md)并进入PIN码认证。具体的场景介绍，请参考[UKey PIN码认证介绍及规格](huks-ukey-pin-authentication-management-overview.md)。

## 开发步骤

1. [打开资源](huks-open-close-resource-ndk.md)。

2. 构造参数，必传[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)和[HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)。

3. 调用接口[authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin)验证PIN码。

## 开发案例

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

// uid由调用方自己获取
let uid: number = 3511;

async function authUkeyPin(): Promise<void> {
  try {
    /* 1.假设已打开的资源如下 */
    const testResourceId = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: {
      key: "testKey"
    } as ESObject
  });

    /* 2.构造参数 */
    const pin = "123456";
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID,
        value: uid
      }, {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
        value: StringToUint8Array(pin)
      }
    ];

    /* 3.验证PIN码 */
    await huksExternalCrypto.authUkeyPin(testResourceId, extProperties)
      .then(() => {
        console.info('promise: getUkeyPinAuthState success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: getUkeyPinAuthState failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: getUkeyPinAuthState input arg invalid.');
  }
}

async function TestAuthUkeyPin() {
  await authUkeyPin();
}
```