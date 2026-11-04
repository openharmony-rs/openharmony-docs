# PIN Access Control

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=e50cd391e32ff59430fc2cd953e8729c4d27fda7 translatedAt=2026-11-03T05:16:31.259Z pushedAt=2026-11-03T06:54:56.720Z nl=1 -->

A PIN (Personal Identification Number) is a security access credential in the Key Management Extension Service. The service implementer can adopt a two-factor authentication mode of "credential + PIN": the user must possess both a valid credential (such as a physical device or a virtual service session) and the correct PIN to access the key material within the service.

The PIN provides the following functions:

1. Brute-force protection: After a certain number of consecutive incorrect entries (depending on the Key Management Extension Service implementation), the PIN is automatically locked. The remaining retry count can be queried through the retryCount field in the return value of [onAuthUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onauthukeypin).

2. Hardware-level security: PIN verification is completed within the Key Management Extension Service, and sensitive information does not leave the service.

The Key Management Extension Service uses resourceId to identify resources. After an ecosystem app opens a resource, if the app needs to perform a signing operation on the private key corresponding to the resourceId, it must verify the PIN first.

## PIN Authentication Status Management

HUKS provides the following PIN authentication status management capabilities:

- **Querying the authentication status**: Starting from API version 22, you can call [getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate) to query the current PIN authentication status.

- **Clearing the authentication status**: Since API version 26.0.0, you can use [clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate) to clear the PIN authentication status of a specified resource.
<!--Del-->
      
- **PIN authentication**: Starting from API version 22, you can call [authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin) to initiate a PIN verification request.
<!--DelEnd-->

> **NOTE**
>
> HUKS provides the PIN authentication and authentication status query capabilities. Before the PIN authentication, you can query its authentication status. If PIN authentication is required, the [certificate management for applications](../DeviceCertificateKit/certManager-overview.md) needs to be started.

## Query Authentication Status

An application can query whether PIN authentication has passed through the corresponding API.

### How to Develop

**ArkTS API**

1. Obtain the resourceId through the [Get Resource ID](huks-extension-ability-general-operation.md#obtaining-resource-id) operation, and pass the resourceId to open the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Call [getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate) to verify the PIN.

3. After the operation is executed, close the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

**C++ API**

1. Link the dynamic libraries in the CMake script:
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. Obtain the resourceId through the certificate management approach in [Get Resource ID](huks-extension-ability-general-operation.md#obtaining-resource-id), and pass the resourceId to open the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

3. Call [OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset) to set specified parameters.

4. Call [OH_Huks_GetUkeyPinAuthState](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getukeypinauthstate) to obtain the PIN authentication status.

5. After the operation is executed, close the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

### Development Cases

**ArkTS API**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getUkeyPinAuthState(): Promise<huksExternalCrypto.HuksExternalPinAuthState> {
  let ret: huksExternalCrypto.HuksExternalPinAuthState = huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH;
  try {
    /* 1. Construct parameters for querying the PIN status. */
    const testResourceId = JSON.stringify({
      providerName: 'testProviderName',
      bundleName: 'com.example.cryptoapplication',
      abilityName: 'CryptoExtension',
      index: {
        key: 'testKey'
      } as ESObject
    });

    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

    /* 2. Call getUkeyPinAuthState. */
    await huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
      .then((data) => {
        console.info(`promise: getUkeyPinAuthState success , data: ${data}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: getUkeyPinAuthState failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: getUkeyPinAuthState input arg invalid.');
  }
  return ret;
}

async function testGetUkeyPinAuthState() {
  let ret: huksExternalCrypto.HuksExternalPinAuthState = await getUkeyPinAuthState();
  if (ret != huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED) {
    console.error('getUkeyPinAuthState failed.');
    return;
  }

  console.info('getUkeyPinAuthState success.');
}
```

**C++ API**

```c++
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>

OH_Huks_Result InitParamSet(
    struct OH_Huks_ExternalCryptoParamSet **paramSet,
    const struct OH_Huks_ExternalCryptoParam *params,
    uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitExternalCryptoParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddExternalCryptoParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeExternalCryptoParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildExternalCryptoParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeExternalCryptoParamSet(paramSet);
        return ret;
    }
    return ret;
}

static const char *resourceId = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\",\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static struct OH_Huks_ExternalCryptoParam g_getPinStateParamsTest[] = {};

static napi_value GetUkeyPinAuthState(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob g_resourceId = {
        (uint32_t)strlen(resourceId),
        (uint8_t *)resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *pinStateParamSet = nullptr;
    OH_Huks_ExternalPinAuthState authState = OH_HUKS_EXT_CRYPTO_PIN_NO_AUTH;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&pinStateParamSet, g_getPinStateParamsTest,
            sizeof(g_getPinStateParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_GetUkeyPinAuthState(&g_resourceId, pinStateParamSet, &authState);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&pinStateParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## Clear Authentication Status

After a key operation is complete or when the authentication status needs to be reset, an application can call the corresponding API to clear the PIN authentication status of a specified resource.

### When to Use

The PIN authentication status may need to be cleared in the following scenarios:

- After a key operation is complete, the authentication status is proactively cleared to avoid residual authentication status.
- Clear the authentication status when the application exits or the user is switched.
- Reset the authentication status when it is abnormal.

### How to Develop

1. Obtain the resourceId through the [Get Resource ID](huks-extension-ability-general-operation.md#obtaining-resource-id) operation, and pass this resourceId to open the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Call [clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate) to clear the PIN authentication status.

3. After the operation is complete, close the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

### Development Cases

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Clear the PIN authentication status.
async function clearUkeyPinAuthState(resourceId: string): Promise<void> {
  try {
    await huksExternalCrypto.clearUkeyPinAuthState(resourceId)
      .then(() => {
        console.info('promise: clearUkeyPinAuthState success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: clearUkeyPinAuthState failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: clearUkeyPinAuthState input arg invalid.');
  }
}
```
<!--Del-->
## PIN Authentication

After the user enters the PIN, the application can call the corresponding API to complete PIN authentication. Before initiating the PIN authentication process, the caller needs to first obtain the public key from the Key Management Extension Service to encrypt the PIN entered by the user. Call the [getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty) API and pass in SKF_ExportPublicKey as the propertyId.

### How to Develop

1. Obtain the resourceId through the [Get Resource ID](huks-extension-ability-general-operation.md#obtaining-resource-id) operation, and pass in this resourceId to open the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Call [getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty) and pass in SKF_ExportPublicKey as the propertyId to export the public key used for encrypted transmission of the PIN.

3. Construct parameters, among which [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) and [HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) are mandatory.

4. Call [authUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto-sys.md#huksexternalcryptoauthukeypin) to verify the PIN.

5. After the operation is complete, close the resource. For details, see [Open/Close Resource](huks-extension-ability-general-operation.md#opening-and-closing-resources).

### Development Cases

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

// The uid is obtained by the caller.
let uid: number = 3511;

async function authUkeyPin(): Promise<void> {
  try {
    /* 1. Assume the resource has been opened as follows. */
    const testResourceId = JSON.stringify({
      providerName: 'testProviderName',
      bundleName: 'com.example.cryptoapplication',
      abilityName: 'CryptoExtension',
      index: {
        key: 'testKey'
      } as ESObject
    });

    /* 2. Construct the parameters. */
    const pin ='123456';
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID,
        value: uid
      }, {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
        value: stringToUint8Array(pin)
      }
    ];

    /* 3. Verify the PIN. */
    await huksExternalCrypto.authUkeyPin(testResourceId, extProperties)
      .then(() => {
        console.info('promise: authUkeyPin success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: authUkeyPin failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: authUkeyPin input arg invalid.');
  }
}

async function testAuthUkeyPin() {
  await authUkeyPin();
}
```
<!--DelEnd-->
<!--no_check-->