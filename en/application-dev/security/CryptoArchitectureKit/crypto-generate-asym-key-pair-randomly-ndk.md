# Randomly Generating an Asymmetric Key Pair (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

This topic uses RSA and SM2 as an example to describe how to generate an asymmetric key pair (**OH_CryptoKeyPair**) and obtain the binary data.

The asymmetric key pair may be used for subsequent operations such as encryption and decryption, and binary data may be used for storage or transmission.

## Adding the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## Randomly Generating an RSA Key Pair

For details about the algorithm specifications, see [RSA](crypto-asym-key-generation-conversion-spec.md#rsa).

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) with the string parameter **'RSA1024|PRIMES_2'** to create an asymmetric key generator (**OH_CryptoAsymKeyGenerator**) for a 1024-bit RSA key with two primes.

2. Call [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to randomly generate an asymmetric key object (**OH_CryptoKeyPair**).

3. Call [OH_CryptoPubKey_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptopubkey_encode) to obtain the binary data of the public key object.

<!-- @[generate_rsa_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateAsymmetricKeyPair/entry/src/main/cpp/types/project/rsa.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_asym_key.h"
#include "file.h"

OH_Crypto_ErrCode generateRSAKey()
{
    OH_CryptoAsymKeyGenerator *ctx = nullptr;
    OH_CryptoKeyPair *keyPair = nullptr;
    OH_Crypto_ErrCode ret;

    ret = OH_CryptoAsymKeyGenerator_Create("RSA1024|PRIMES_2", &ctx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(ctx);
        return ret;
    }
    
    ret = OH_CryptoAsymKeyGenerator_Generate(ctx, &keyPair);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(ctx);
        OH_CryptoKeyPair_Destroy(keyPair);
        return ret;
    }

    OH_CryptoPubKey *pubKey = OH_CryptoKeyPair_GetPubKey(keyPair);
    Crypto_DataBlob retBlob = {.data = nullptr, .len = 0};
    ret = OH_CryptoPubKey_Encode(pubKey, CRYPTO_PEM, "PKCS1", &retBlob);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(ctx);
        OH_CryptoKeyPair_Destroy(keyPair);
        return ret;
    }

    OH_Crypto_FreeDataBlob(&retBlob);

    OH_CryptoAsymKeyGenerator_Destroy(ctx);
    OH_CryptoKeyPair_Destroy(keyPair);
    return ret;
}
```


## Randomly Generating an SM2 Key Pair

For details about the algorithm specifications, see [SM2](crypto-asym-key-generation-conversion-spec.md#sm2).

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) with the string parameter **'SM2_256'** to create an asymmetric key generator (**OH_CryptoAsymKeyGenerator**) object for a 256-bit SM2 key.

2. Call [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to randomly generate an asymmetric key object (**OH_CryptoKeyPair**).

3. Call [OH_CryptoPubKey_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptopubkey_encode) to obtain the binary data of the public key object.

<!-- @[generate_sm2_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/RandomlyGenerateAsymmetricKeyPair/entry/src/main/cpp/types/project/sm2.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_asym_key.h"
#include "file.h"

OH_Crypto_ErrCode generateSM2Key()
{
    OH_CryptoAsymKeyGenerator *ctx = nullptr;
    OH_CryptoKeyPair *dupKeyPair = nullptr;
    OH_Crypto_ErrCode ret;

    ret = OH_CryptoAsymKeyGenerator_Create("SM2_256", &ctx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(ctx);
        return ret;
    }

    ret = OH_CryptoAsymKeyGenerator_Generate(ctx, &dupKeyPair);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(ctx);
        OH_CryptoKeyPair_Destroy(dupKeyPair);
        return ret;
    }

    OH_CryptoPubKey *pubKey = OH_CryptoKeyPair_GetPubKey(dupKeyPair);
    Crypto_DataBlob retBlob = { .data = nullptr, .len = 0 };
    ret = OH_CryptoPubKey_Encode(pubKey, CRYPTO_DER, nullptr, &retBlob);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoAsymKeyGenerator_Destroy(ctx);
        OH_CryptoKeyPair_Destroy(dupKeyPair);
        return ret;
    }

    OH_Crypto_FreeDataBlob(&retBlob);
    OH_CryptoAsymKeyGenerator_Destroy(ctx);
    OH_CryptoKeyPair_Destroy(dupKeyPair);
    return ret;
}
```
