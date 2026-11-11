# Signing and Signature Verification

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f70f62268656d3b182431efa45d33eb33ec094f1 translatedAt=2026-11-10T03:03:07.853Z pushedAt=2026-11-10T06:41:58.409Z nl=1 -->

In the key management extension scenario, after completing key management extension PIN authentication, an application can operate the corresponding key through resourceId to perform signing and signature verification operations. This capability is implemented through the three-phase API provided by HUKS. The application only needs to specify the corresponding algorithm parameters (including algorithm type, purpose, padding, digest, etc.).

## Three-Phase API Description

Signing/signature verification operations are implemented through the HUKS three-phase APIs. Setting [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to [HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22) indicates that the specified key is a key from the key management extension service.

For specific usage, refer to [Signing/Signature Verification Example](#signingsignature-verification-example).

| Step | API | Description |
|------|------|------|
| 1 | [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) | Initializes a key session and returns the session handle. |
| 2 | [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) | (Optional) Passes segmented data and performs intermediate cryptographic operations. |
| 3 | [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) | Ends the session and returns the final result (signature/signature verification result). |

> **NOTE**
>
> 1. By setting [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to [HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22), it indicates that the key is managed by an external key management extension.
> 2. During the three-phase operation, the keyAlias parameter must be specified as resourceId.
> 3. After finishSession completes, the session handle is released.
> 4. Whether signing/signature verification requires PIN authentication depends on the key purpose: private key signing requires PIN authentication, while public key signature verification does not.

## Specifications

The specifications are related to the implementation of the external hardware key management extension, which vary according to vendors.

Signature/signature verification operations require the following parameters to be specified in HuksOptions.properties:

### Detailed Parameters

| Parameter | Value | Mandatory | Description |
|------|------|------|------|
| [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | `HUKS_KEY_CLASS_EXTENSION` | Yes | Indicates that the key is managed by the key management extension |
| [HUKS_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | Purpose enumeration value | No | Specifies the purpose. If not passed, the default value provided by the key management extension is used |
| [HUKS_TAG_ALGORITHM](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | Algorithm enumeration value | No | Specifies the signature/signature verification algorithm |
| [HUKS_TAG_KEY_SIZE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | Key length | No | For example, 2048, 3072, 4096 |

## Signing/Signature Verification Example

The following example uses a key with the RSA algorithm, SHA256 digest algorithm, and PSS padding mode to complete signing and signature verification:

### How to Develop

**ArkTS API**

**Signing:**

1. Obtain the resourceId through the [obtaining a resource ID](huks-extension-ability-general-operation.md#obtaining-a-resource-id) operation, and pass the resourceId to open the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Complete PIN authentication by referring to [PIN access control](huks-extension-ability-pin-authentication-management.md).

3. Set the property parameter [HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions), and pass the algorithm parameter configuration in properties.

4. Use [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session without passing inData, and get the sessionHandle.

5. (Optional) Use [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) to update the key session, and pass the plaintext data in inData.

6. Use [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to end the session, pass the plaintext data in inData, and get the signature from outData in the return value.

7. After the operation is complete, close the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

**Signature Verification:**

1. Obtain the resourceId through the [obtaining a resource ID](huks-extension-ability-general-operation.md#obtaining-a-resource-id) operation, and pass the resourceId to open the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Set the property parameter [HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions), and pass the algorithm parameter configuration in properties.

3. Use [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session without passing inData, and get the sessionHandle.

4. (Optional) Use [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) to update the session, and pass the plaintext data in inData.

5. Use [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to end the session, and pass the signature in inData.

6. After the operation is complete, close the resource. For details, see [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

**C++ APIs**

**Signing:**

1. Obtain [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22) as the resourceId through [openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) provided by the certificate management system capability, use it as the key alias, open the resource, and then complete PIN authentication. For details, refer to [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Obtain the plaintext to be signed.

3. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to specify the algorithm parameter configuration, and specify the KeyClass parameter, with the tag being [OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) and the value being [OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype).

4. Use [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Use [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to end the key session and obtain the signature.

**Signature Verification:**

1. Obtain [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22) as the resourceId through [openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) provided by the certificate management system capability, use it as the key alias, and then open the resource. For details, refer to [Opening and Closing Resources](huks-extension-ability-general-operation.md#opening-and-closing-resources).

2. Obtain the signature to be verified.

3. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to specify the algorithm parameter configuration, and specify the KeyClass parameter, with the tag being [OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) and the value being [OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype).

4. Use [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Use [OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession) to update the key session.

6. Use [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to end the key session and verify the signature.

### Development Examples

**ArkTS API**

<!-- @[ukey_sign_verify_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/SignVerify.ets) -->

``` TypeScript
/*
 * The key algorithm is RSA, the digest algorithm is SHA256, and the padding mode is PSS.
 */
import { huks, huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

let handle: number;
let plaintext = '123456';
let signature: Uint8Array;

function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

interface HuksProperty {
    tag: huks.HuksTag;
    value: number;
}

function getRsaSignProperties(): HuksProperty[] {
  return [
    { tag: huks.HuksTag.HUKS_TAG_ALGORITHM, value: huks.HuksKeyAlg.HUKS_ALG_RSA },
    { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048 },
    { tag: huks.HuksTag.HUKS_TAG_PADDING, value: huks.HuksKeyPadding.HUKS_PADDING_PSS },
    { tag: huks.HuksTag.HUKS_TAG_DIGEST, value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256 },
    { tag: huks.HuksTag.HUKS_TAG_PURPOSE, value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN },
    { tag: huks.HuksTag.HUKS_TAG_KEY_CLASS, value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION }
  ];
}

function getRsaVerifyProperties(): HuksProperty[] {
  return [
    { tag: huks.HuksTag.HUKS_TAG_ALGORITHM, value: huks.HuksKeyAlg.HUKS_ALG_RSA },
    { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048 },
    { tag: huks.HuksTag.HUKS_TAG_PADDING, value: huks.HuksKeyPadding.HUKS_PADDING_PSS },
    { tag: huks.HuksTag.HUKS_TAG_DIGEST, value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256 },
    { tag: huks.HuksTag.HUKS_TAG_PURPOSE, value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY },
    { tag: huks.HuksTag.HUKS_TAG_KEY_CLASS, value: huks.HuksKeyClassType.HUKS_KEY_CLASS_EXTENSION }
  ];
}

async function initSession(keyAlias: string, options: huks.HuksOptions) {
  await huks.initSession(keyAlias, options)
    .then((data) => { handle = data.handle; })
    .catch((error: BusinessError) => console.error(`initSession failed: ${error.code}`));
}

async function finishSession(options: huks.HuksOptions) {
  await huks.finishSession(handle, options)
    .then((data) => { signature = data.outData as Uint8Array; });
}

async function sign(keyAlias: string) {
  const options: huks.HuksOptions = { properties: getRsaSignProperties() };
  await initSession(keyAlias, options);
  if (handle !== undefined) {
    options.inData = stringToUint8Array(plaintext);
    await finishSession(options);
  }
}

async function verify(keyAlias: string) {
  const options: huks.HuksOptions = { properties: getRsaVerifyProperties() };
  await initSession(keyAlias, options);
  if (handle !== undefined) {
    options.inData = stringToUint8Array(plaintext);
    await huks.updateSession(handle, options);
    options.inData = signature;
    await huks.finishSession(handle, options);
  }
}

async function signAndVerify() {
  const keyAlias = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: { key: 'testKey' } as ESObject
  });
  try {
    // Signing process.
    await huksExternalCrypto.openResource(keyAlias);
    // Perform PIN authentication.
    await sign(keyAlias);
    await huksExternalCrypto.closeResource(keyAlias);

    // Signature verification process (no PIN authentication required).
    await huksExternalCrypto.openResource(keyAlias);
    await verify(keyAlias);
    await huksExternalCrypto.closeResource(keyAlias);
  } catch (error) {
    console.error('signAndVerify input arg invalid.');
  }
}
```

**C++ API**

<!-- @[ukey_sign_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
/* Call the HUKS three-phase APIs to obtain the signed data. */
static struct OH_Huks_Param g_signParamsTest[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_RSA
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PSS
    }, {
        .tag = OH_HUKS_TAG_DIGEST,
        .uint32Param = OH_HUKS_DIGEST_SHA384
    }, {
        .tag = OH_HUKS_TAG_KEY_CLASS,
        .uint32Param = OH_HUKS_KEY_CLASS_EXTENSION
    }
};

static const uint32_t RSA_COMMON_SIZE = 1024;
static const char *DATA_TO_SIGN = "testData";
static const char *KEY_ALIAS = "testKeyAlias";

static napi_value Sign(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob keyAlias = {
        (uint32_t)strlen(KEY_ALIAS),
        (uint8_t *)KEY_ALIAS
    };
    struct OH_Huks_Blob inData = {
        (uint32_t)strlen(DATA_TO_SIGN),
        (uint8_t *)DATA_TO_SIGN
    };
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitHuksParamSet(&signParamSet, g_signParamsTest,
            sizeof(g_signParamsTest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        uint8_t handleS[sizeof(uint64_t)] = {0};
        struct OH_Huks_Blob handleSign = { (uint32_t)sizeof(uint64_t), handleS };
        ohResult = OH_Huks_InitSession(&keyAlias, signParamSet, &handleSign, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = { RSA_COMMON_SIZE, outDataS };
        ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeParamSet(&signParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```