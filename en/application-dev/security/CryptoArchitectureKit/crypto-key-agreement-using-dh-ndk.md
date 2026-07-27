# Key Agreement Using DH (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

For details about the algorithm specifications, see [DH](crypto-key-agreement-overview.md#dh).

## How to Develop

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) and [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to generate an asymmetric key (**keyPair**) of the DH_modp1536 type.

   For details about how to generate a DH asymmetric key pair, see the following example. To learn more, see [DH](crypto-asym-key-generation-conversion-spec.md#dh) and [Randomly Generating an Asymmetric Key Pair](crypto-generate-asym-key-pair-randomly-ndk.md). There may be differences between the input parameters in the reference documents and those in the following example.

2. Call [OH_CryptoKeyAgreement_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_create) and specify the string parameter **DH_modp1536** to create a key protocol generator of the DH_modp1536 type.

3. Call [OH_CryptoKeyAgreement_GenerateSecret](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret) to perform key agreement based on the passed private key (**keyPair.priKey**) and public key (**keyPair.pubKey**) and return the shared key.


<!-- @[TestDh](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyNegotiationCpp/entry/src/main/cpp/types/project/DH.cpp) -->

``` C++

#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include "CryptoArchitectureKit/crypto_key_agreement.h"
#include "file.h"
#include <cstdio>
#include <cstring>

static OH_Crypto_ErrCode GenerateSecret(OH_CryptoKeyAgreement *dhKeyAgreement, OH_CryptoKeyPair *keyPairA,
    OH_CryptoKeyPair *keyPairB, Crypto_DataBlob *secret)
{
    OH_CryptoPrivKey *privKey = OH_CryptoKeyPair_GetPrivKey(keyPairA);
    OH_CryptoPubKey *pubKey = OH_CryptoKeyPair_GetPubKey(keyPairB);
    return OH_CryptoKeyAgreement_GenerateSecret(dhKeyAgreement, privKey, pubKey, secret);
}

static OH_Crypto_ErrCode compareSecrets(const Crypto_DataBlob *secret1, const Crypto_DataBlob *secret2)
{
    if ((secret1->len == secret2->len) &&
        (memcmp(secret1->data, secret2->data, secret1->len) == 0)) {
        return CRYPTO_SUCCESS;
    }
    return CRYPTO_OPERTION_ERROR;
}

OH_Crypto_ErrCode doTestDHKeyAgreement()
{
    OH_CryptoAsymKeyGenerator *dhGen = nullptr;
    OH_CryptoKeyPair *keyPairA = nullptr;
    OH_CryptoKeyPair *keyPairB = nullptr;
    OH_CryptoKeyAgreement *dhKeyAgreement = nullptr;
    Crypto_DataBlob secret1 = { 0 };
    Crypto_DataBlob secret2 = { 0 };
    OH_Crypto_ErrCode ret = OH_CryptoAsymKeyGenerator_Create("DH_modp1536", &dhGen);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Generate public-private key pairs A and B.
    ret = OH_CryptoAsymKeyGenerator_Generate(dhGen, &keyPairA);
    if (ret != CRYPTO_SUCCESS) {
        goto goto_cleanup;
    }

    ret = OH_CryptoAsymKeyGenerator_Generate(dhGen, &keyPairB);
    if (ret != CRYPTO_SUCCESS) {
        goto goto_cleanup;
    }

    ret = OH_CryptoKeyAgreement_Create("DH_modp1536", &dhKeyAgreement);
    if (ret != CRYPTO_SUCCESS) {
        goto goto_cleanup;
    }

    // Use the public key of A and the private key of B to perform key agreement.
    ret = GenerateSecret(dhKeyAgreement, keyPairB, keyPairA, &secret1);
    if (ret != CRYPTO_SUCCESS) {
        goto goto_cleanup;
    }

    // Use the public key of B and the private key of A to perform key agreement.
    ret = GenerateSecret(dhKeyAgreement, keyPairA, keyPairB, &secret2);
    if (ret != CRYPTO_SUCCESS) {
        goto goto_cleanup;
    }

    // Compare the secrets.
    ret = compareSecrets(&secret1, &secret2);
    if (ret != CRYPTO_SUCCESS) {
        printf("dh result is not equal\n");
        goto goto_cleanup;
    }

goto_cleanup:
    OH_Crypto_FreeDataBlob(&secret1);
    OH_Crypto_FreeDataBlob(&secret2);
    OH_CryptoKeyAgreement_Destroy(dhKeyAgreement);
    OH_CryptoKeyPair_Destroy(keyPairA);
    OH_CryptoKeyPair_Destroy(keyPairB);
    OH_CryptoAsymKeyGenerator_Destroy(dhGen);
    return ret;
}
```
