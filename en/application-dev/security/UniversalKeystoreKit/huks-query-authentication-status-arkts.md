# Authentication Status Query (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

From API version 22, **huksExternalCrypto** provides the API for querying the PIN authentication status. This API can be used by applications to query whether the PIN passes authentication. For details about the scenarios and specifications, see [Ukey PIN Authentication Management Overview and Specifications](huks-ukey-pin-authentication-management-overview.md).

## How to Develop

1. Obtain [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) as **resourceId** by referring to [certificate management for applications](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22).

2. Call [getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate) to verify the PIN.

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getUkeyPinAuthState(): Promise<huksExternalCrypto.HuksExternalPinAuthState> {
  let ret: huksExternalCrypto.HuksExternalPinAuthState = huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH;
  try {
    /* 1. Construct parameters for querying the PIN status.*/
    const testResourceId = JSON.stringify({
      providerName: "testProviderName",
      bundleName: "com.example.cryptoapplication",
      abilityName: "CryptoExtension",
      index: {
        key: "testKey"
      } as ESObject
    });
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

    /* 2. Call getUkeyPinAuthState. */
    await huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
      .then((data) => {
        console.info(`promise: getUkeyPinAuthState success , data : ${data}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: getUkeyPinAuthState failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error(`promise: getUkeyPinAuthState input arg invalid`);
  }
  return ret;
}

async function testGetUkeyPinAuthState() {
  let ret: huksExternalCrypto.HuksExternalPinAuthState = await getUkeyPinAuthState();
  if (ret != huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED) {
    console.error(`getUkeyPinAuthState failed`);
    return;
  }

  console.info(`getUkeyPinAuthState success`);
}
```
