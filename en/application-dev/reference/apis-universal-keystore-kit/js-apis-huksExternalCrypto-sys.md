# @ohos.security.huksExternalCrypto (External Key Management) (System API)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Provides the functionalities such as registration and deregistration of external key management extension, PIN authentication, and acquisition of authentication state.

> **Description**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## huksExternalCrypto.authUkeyPin

authUkeyPin(resourceId: string, params: Array\<HuksExternalCryptoParam>): Promise\<void>

Authenticates a Ukey PIN. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | -------- | ---- | -------|
| resourceId | string | Yes  | Resource ID of a container in the Ukey, which can be obtained using [certificateManagerDialog.openAuthorizeDialog22+](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22). The result contains **resourceId**.|
| params  | Array\<[HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Parameters to be passed during the operation. The mandatory tag is [HUKS_EXT_CRYPTO_TAG_UKEY_PIN](js-apis-huksExternalCrypto.md#huksexternalcryptotag).|

**Return value**

| Type    | Description  |
| -------- | ---------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [HUKS Error Codes](errorcode-huks.md).

| ID| Error Message     |
| -------- | ------------- |
| 202 | The caller is not a system application and is not allowed to use system applications. |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | the Ukey driver operation failed. |
| 12000011 | queried entity does not exist. |
| 12000012 | Device environment or input parameter abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |
| 12000020 | the provider operation failed. |
| 12000021 | the Ukey PIN is locked. |
| 12000022 | the Ukey PIN is incorrect. |
| 12000024 | the provider or Ukey is busy. |

**Example**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let uid: number = 3511
const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
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
huksExternalCrypto.authUkeyPin(testResourceId, extProperties)
    .then((data) => {
        console.info(`promise: authUkeyPin success`);
    });
```
