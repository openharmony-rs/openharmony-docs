# Ukey PIN Authentication (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

From API version 22, **huksExternalCrypto** provides the PIN authentication API. An ecosystem app calls the certificate HAP UI to display a certificate list. After a user selects a certificate, the browser obtains **resourceId** based on the selected certificate, and then [open the resource](huks-open-close-resource-ndk.md) for PIN authentication. For details about the scenarios, see [Ukey PIN Authentication Overview and Specifications](huks-ukey-pin-authentication-management-overview.md).

## How to Develop

1. [Open the resource](huks-open-close-resource-ndk.md).

2. Construct parameters, among which [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) and [HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) are mandatory.

3. Call [authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin) to verify the PIN.

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

// The UID is obtained by the caller.
let uid: number = 3511;

async function authUkeyPin(): Promise<void> {
  try {
    /* 1. Assume that the opened resources are as follows: */
    const testResourceId = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: {
      key: "testKey"
    } as ESObject
  });

    /* 2. Construct parameters. */
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

    /* 3. Verify the PIN. */
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
