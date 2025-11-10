# Key Derivation Using X963KDF (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

From API version 22, the crypto algorithm library supports key derivation with X963KDF.

For details about the corresponding algorithm specifications, see [X963KDF](crypto-key-derivation-overview.md#x963kdf).

## How to Develop

1. Call [OH_CryptoKdfParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdfparams_create) and specify the string parameter **X963KDF** to create a key derivation parameter object.

2. Call [OH_CryptoKdfParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdfparams_setparam) to set the parameters required by X963KDF. Example:
   - **CRYPTO_KDF_KEY_DATABLOB**: original key material used to generate a derived key.
   - **CRYPTO_KDF_INFO_DATABLOB**: (optional) application-specific information.

3. Call [OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create) and specify the string parameter **X963KDF|SHA256** to create a key derivation function object.

4. Call [OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive) and specify the byte length of the target key.

```C++
#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <stdio.h>
#include <string.h>

static OH_Crypto_ErrCode doTestX963Kdf()
{
    // Create a X963KDF parameter object.
    OH_CryptoKdfParams *params = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoKdfParams_Create("X963KDF", &params);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Set the original key material.
    const char *keyData = "012345678901234567890123456789";
    Crypto_DataBlob key = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(keyData)),
        .len = strlen(keyData)
    };
    ret = OH_CryptoKdfParams_SetParam(params, CRYPTO_KDF_KEY_DATABLOB, &key);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }


    // Set application-specific information.
    const char *infoData = "infostring";
    Crypto_DataBlob info = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(infoData)),
        .len = strlen(infoData)
    };
    ret = OH_CryptoKdfParams_SetParam(params, CRYPTO_KDF_INFO_DATABLOB, &info);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }

    // Create a key derivation function object.
    OH_CryptoKdf *kdfCtx = nullptr;
    ret = OH_CryptoKdf_Create("X963KDF|SHA256", &kdfCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }

    // Derive a key.
    Crypto_DataBlob out = {0};
    uint32_t keyLength = 32; // Generate a 32-byte key.
    ret = OH_CryptoKdf_Derive(kdfCtx, params, keyLength, &out);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdf_Destroy(kdfCtx);
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }

    printf("Derived key length: %u\n", out.len);

    // Free resources.
    OH_Crypto_FreeDataBlob(&out);
    OH_CryptoKdf_Destroy(kdfCtx);
    OH_CryptoKdfParams_Destroy(params);
    return CRYPTO_SUCCESS;
}
```
