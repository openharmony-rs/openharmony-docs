# Clearing the PIN Authentication Status (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Since API version 26.0.0, **huksExternalCrypto** provides the API for clearing the PIN authentication status. After a key operation is complete or when the authentication status needs to be reset, an application can call this API to clear the PIN authentication status of a specified resource. For details about the scenarios and specifications, see [Ukey PIN Authentication Management Overview and Specifications](huks-ukey-pin-authentication-management-overview.md).

## Development Procedure

1. Obtain the resource ID. You can obtain the key URI as the resource ID by calling the [certificate selection API](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22) or obtain the resource ID extended by the external key manager by calling [getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid).

2. Call [clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate) to clear the PIN authentication status.

## Development Cases

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Clear the PIN authentication status (ArkTS)
async function clearUkeyPinAuthState(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.clearUkeyPinAuthState(resourceId)
      .then(() => {
        console.info('promise: clearUkeyPinAuthState success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: clearUkeyPinAuthState failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: clearUkeyPinAuthState input arg invalid.');
  }
}
```
<!--no_check-->