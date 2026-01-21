# Generating Secure Random Numbers with Hardware Entropy Sources (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

From API version 21, you can generate secure random number with hardware entropy sources.

Random numbers are used to generate temporary session keys and asymmetric encryption algorithm keys. In encryption and decryption, a secure random number generator must feature randomness, unrepeatability, and unpredictability.

A stronger entropy source makes random numbers harder to predict or replicate, achieving true randomness.
<!--Del-->You need to use HUKS for generating random numbers with hardware entropy sources. For systems or devices with a secure environment (such as TEE and secure chip), after the hardware entropy source is enabled, the secure random number (with hardware entropy source) is obtained from the TEE through HUKS as the entropy source of the algorithm library. The secure environment depends on the hardware. The implementation in the open source repository is simulated, and subject to adaptation by OEM vendors.<!--DelEnd-->

You need to call the related APIs of [HUKS](../../../application-dev/security/UniversalKeystoreKit/huks-overview.md) to implement the hardware entropy source.

You can call APIs to:

- Generate a secure random number of the specified length and use it to generate a key.

- Enable the hardware entropy source.

- Generate a series of random sequences based on a seed.

It will be helpful if you have basic knowledge of encryption and decryption and understand the following basic concepts:

- **Internal state**

  A value in the random number generator memory. The same internal state produces a random number of the same sequence.

- **Random seed**

  A number used to initialize the internal state of a pseudorandom number generator. The random number generator generates a series of random sequences based on the seeds.

  In the OpenSSL implementation, the internal state of the random number generator changes continuously. Therefore, the generated random number sequences are different even if the same seed is used.

## Supported Algorithms and Specifications

After the hardware entropy source is set, use the **RAND_priv_bytes** API of OpenSSL to generate secure random numbers.

| Algorithm| Length (Byte)|
| -------- | -------- |
| CTR_DRBG | [1, INT_MAX] |

## How to Develop

1. Call [OH_CryptoRand_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-rand-h.md#oh_cryptorand_create) to create a random number generator.

2. Call [OH_CryptoRand_EnableHardwareEntropy](../../reference/apis-crypto-architecture-kit/capi-crypto-rand-h.md#oh_cryptorand_enablehardwareentropy) to enable the hardware entropy source.

3. (Optional) Call [OH_CryptoRand_SetSeed](../../reference/apis-crypto-architecture-kit/capi-crypto-rand-h.md#oh_cryptorand_setseed) to set a seed for the random number generator.

4. Call [OH_CryptoRand_GenerateRandom](../../reference/apis-crypto-architecture-kit/capi-crypto-rand-h.md#oh_cryptorand_generaterandom) to generate a secure random number of the given length. The length of the random number to generate ranges from **1** to **INT_MAX**, in bytes.

5. Call [OH_CryptoRand_GetAlgoName](../../reference/apis-crypto-architecture-kit/capi-crypto-rand-h.md#oh_cryptorand_getalgoname) to obtain the algorithm name used by the random number generator.

```C++
#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <stdio.h>

static OH_Crypto_ErrCode doTestRandomNumber()
{
    // Create a random number generator.
    OH_CryptoRand *rand = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoRand_Create(&rand);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Enable the hardware entropy source.
    ret = OH_CryptoRand_EnableHardwareEntropy(rand);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoRand_Destroy(rand);
        return ret;
    }

    // (Optional) Set the random seed.
    uint8_t seedData[12] = {0x25, 0x65, 0x58, 0x89, 0x85, 0x55, 0x66, 0x77, 0x88, 0x99, 0x11, 0x22};
    Crypto_DataBlob seed = {
        .data = seedData,
        .len = sizeof(seedData)
    };
    ret = OH_CryptoRand_SetSeed(rand, &seed);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoRand_Destroy(rand);
        return ret;
    }

    // Generate a random number of the given length.
    Crypto_DataBlob out = {0};
    uint32_t randomLength = 24; // Generate a 24-byte random number.
    ret = OH_CryptoRand_GenerateRandom(rand, randomLength, &out);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoRand_Destroy(rand);
        return ret;
    }

    // Obtain and print the algorithm name of the random number generator.
    const char *algoName = OH_CryptoRand_GetAlgoName(rand);
    if (algoName != nullptr) {
        printf("Random number generator algorithm: %s\n", algoName);
    }

    printf("Generated random number length: %u\n", out.len);

    // Free resources.
    OH_Crypto_FreeDataBlob(&out);
    OH_CryptoRand_Destroy(rand);
    return CRYPTO_SUCCESS;
}
```
