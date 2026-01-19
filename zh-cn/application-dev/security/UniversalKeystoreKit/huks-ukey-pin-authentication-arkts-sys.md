# Ukey PIN码认证(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API 22开始，huksExternalCrypto提供PIN码认证功能接口。生态应用调用证书HAP界面，展示证书列表，用户选择证书后，浏览器根据选择的证书获取到resourceId，然后[打开资源](huks-open-close-resource-ndk.md)并进入PIN码认证。具体的场景介绍，请参考[Ukey PIN码认证介绍及规格](huks-ukey-pin-authentication-management-overview.md)。

## 开发步骤

1. [打开资源](huks-open-close-resource-ndk.md)。

2. 构造参数，必传[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)和[HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)。

3. 调用接口[authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin)验证PIN码。

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
        console.info(`promise: getUkeyPinAuthState success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: getUkeyPinAuthState failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: getUkeyPinAuthState input arg invalid`);
  }
}

async function TestAuthUkeyPin() {
  await authUkeyPin();
}
```