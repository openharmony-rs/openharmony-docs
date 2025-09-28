# Converting Binary Data into a Symmetric Key Pair (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

This topic uses 3DES and HMAC as an example to describe how to convert binary data into a symmetric key (**OH_CryptoSymKey**). That is, convert a piece of external or internal binary data into a key object for subsequent operations, such as encryption and decryption.

## Adding the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## Converting Binary Data into a 3DES Key

For details, see [3DES](crypto-sym-key-generation-conversion-spec.md#3des).

1. Obtain the 3DES binary key data and encapsulate it into a [Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md) object.

2. Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) with the string parameter **'3DES192'** to create a symmetric key generator (**OH_CryptoSymKeyGenerator**) object for a 192-bit 3DES key.

3. Call [OH_CryptoSymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_convert) to convert the binary data into a symmetric key object (**OH_CryptoSymKey**).

4. Call [OH_CryptoSymKey_GetKeyData](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_getkeydata) to obtain the binary data of the key object.

Example: Convert binary data into a 3DES key.

  ```c++
  #include "CryptoArchitectureKit/crypto_common.h"
  #include "CryptoArchitectureKit/crypto_sym_key.h"

  static OH_Crypto_ErrCode doTestDataCovertSymKey() {
      const char *algName = "3DES192";
      OH_CryptoSymKeyGenerator *ctx = nullptr;
      OH_CryptoSymKey *convertKeyCtx = nullptr;
      Crypto_DataBlob out = {.data = nullptr, .len = 0};
      OH_Crypto_ErrCode ret;
      uint8_t arr[] = {0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56, 0xad, 0x47, 0xfc, 0x5a,
                      0x46, 0x39, 0xee, 0x7c, 0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72};
      Crypto_DataBlob convertBlob = {.data = arr, .len = sizeof(arr)};
      ret = OH_CryptoSymKeyGenerator_Create(algName, &ctx);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
      ret = OH_CryptoSymKeyGenerator_Convert(ctx, &convertBlob, &convertKeyCtx);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoSymKeyGenerator_Destroy(ctx);
          return ret;
      }
      ret = OH_CryptoSymKey_GetKeyData(convertKeyCtx, &out);
      OH_CryptoSymKeyGenerator_Destroy(ctx);
      OH_CryptoSymKey_Destroy(convertKeyCtx);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
      OH_Crypto_FreeDataBlob(&out);
      return ret;
  }
  ```

## Converting Binary Data into an HMAC Key

For details, see [HMAC](crypto-sym-key-generation-conversion-spec.md#hmac).

1. Obtain the HMAC binary key and encapsulate it into a [Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md) object.

2. Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) with the string parameter **'HMAC'** to create a symmetric key generator (**OH_CryptoSymKeyGenerator**) object for a 32768-bit HMAC key.

3. Call [OH_CryptoSymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_convert) to convert the binary data into a symmetric key object (**OH_CryptoSymKey**).

4. Call [OH_CryptoSymKey_GetKeyData](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_getkeydata) to obtain the binary data of the key object.

Example: Convert binary data into an HMAC key.

  ```c++
  #include "CryptoArchitectureKit/crypto_common.h"
  #include "CryptoArchitectureKit/crypto_sym_key.h"
  #include <string.h>

  static OH_Crypto_ErrCode testConvertHmacKey() {
      const char *algName = "HMAC";
      OH_CryptoSymKeyGenerator *ctx = nullptr;
      OH_CryptoSymKey *convertKeyCtx = nullptr;
      Crypto_DataBlob out = {.data = nullptr, .len = 0};
      OH_Crypto_ErrCode ret;

      char *arr = const_cast<char *>("12345678abcdefgh12345678abcdefgh12345678abcdefgh12345678abcdefgh");
      Crypto_DataBlob convertBlob = {.data = (uint8_t *)(arr), .len = strlen(arr)};
      ret = OH_CryptoSymKeyGenerator_Create(algName, &ctx);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
      ret = OH_CryptoSymKeyGenerator_Convert(ctx, &convertBlob, &convertKeyCtx);
      if (ret != CRYPTO_SUCCESS) {
          OH_CryptoSymKeyGenerator_Destroy(ctx);
          return ret;
      }
      ret = OH_CryptoSymKey_GetKeyData(convertKeyCtx, &out);
      OH_CryptoSymKeyGenerator_Destroy(ctx);
      OH_CryptoSymKey_Destroy(convertKeyCtx);
      if (ret != CRYPTO_SUCCESS) {
          return ret;
      }
      OH_Crypto_FreeDataBlob(&out);
      return ret;
  }
  ```
