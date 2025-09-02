# Symmetric Key Encryption and Decryption Algorithm Specifications

This topic describes the supported algorithms and specifications for symmetric key encryption and decryption.

For details about the cipher modes supported by each algorithm, see the specifications of each algorithm.

## AES

The Crypto framework provides the following cipher modes for [AES](crypto-sym-key-generation-conversion-spec.md#aes) encryption and decryption: ECB, CBC, OFB, CFB, CTR, GCM, and CCM. The encryption and decryption parameters vary depending on the cipher mode. For details, see [ParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#paramsspec).

AES is a block cipher, with a fixed block size of 128 bits. If the last block is less than 128 bits (16 bytes), you can specify the [padding mode](#padding-mode) to pad data.

Because the data is padded to the block size, **PKCS5** and **PKCS7** used in the Crypto framework use the block size as the padding length. That is, data is padded to 16 bytes for AES encryption.

> **NOTE**
>
> In ECB and CBC modes, the plaintext must be padded if its length is not an integer multiple of 128 bits.
> In CCM encryption mode, the additional authentication data (AAD) must be specified and its length must be greater than 1 byte and less than 2048 bytes.

The AES encryption and decryption can be implemented based a string parameter. When creating a **Cipher** instance, you need to specify the algorithm specifications in a string parameter. The string parameter consists of the symmetric key type (algorithm and key length), cipher block mode, and padding mode with a vertical bar (|) in between.

- In the following table, the options included in the square brackets ([]) are mutually exclusive. You can use only one of them in a string parameter.
  
  Example:
  - If the cipher block mode is ECB and padding mode is **PKCS7** for a 128-bit AES key, the string parameter is **AES128|ECB|PKCS7**.
  
  - If the cipher block mode is CFB and padding mode is **NoPadding** for a 256-bit AES key, the string parameter is **AES256|CFB|NoPadding**.

  | Cipher Mode| Key Length (Bit)| Padding Mode| API Version| 
  | -------- | -------- | -------- | -------- |
  | ECB | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | CBC | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | CTR | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | OFB | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | CFB | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | GCM | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | CCM | [128\|192\|256] | [NoPadding\|PKCS5\|PKCS7] | 9+ | 

- Since API version 10, symmetric encryption and decryption support the algorithm specifications without the key length. If the symmetric key type does not contain the key length, the encryption and decryption operations vary with the actual key length.
  
  For example, if the block mode is CFB and the padding mode is **NoPadding** for an AES key with key length not specified, the string parameter is **AES|CFB|NoPadding**.

## 3DES

[3DES](crypto-sym-key-generation-conversion-spec.md#3des) encryption and decryption apply the DES cipher three times to each data block to obtain the ciphertext or plaintext.

The Crypto framework provides the following cipher modes for 3DES encryption and decryption: ECB, CBC, OFB, and CFB. The encryption and decryption parameters vary depending on the cipher mode. For details, see [ParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#paramsspec).

DES is a block cipher, with a fixed block size of 64 bits. If the last block is less than 64 bits (8 bytes), you can specify the [padding mode](#padding-mode) to pad data.

Because the data is padded to the block size, **PKCS5** and **PKCS7** used in the Crypto framework use the block size as the padding length. That is, data is padded to 8 bytes for 3DES encryption.

> **NOTE**
>
> In ECB and CBC modes, the plaintext must be padded if its length is not an integer multiple of 64 bits.

The 3DES encryption and decryption can be implemented based a string parameter. When creating a **Cipher** instance, you need to specify the algorithm specifications in a string parameter. The string parameter consists of the symmetric key type (algorithm and key length), cipher block mode, and padding mode with a vertical bar (|) in between.

- In the following table, the options included in the square brackets ([]) are mutually exclusive. You can use only one of them in a string parameter.
  
  Example:
  - If the cipher block mode is ECB and padding mode is **PKCS7** for a 192-bit 3DES key, the string parameter is **3DES192|ECB|PKCS7**.
  
  - If the cipher block mode is OFB and padding mode is **NoPadding** for a 192-bit 3DES key, the string parameter is **3DES192|OFB|NoPadding**.

  | Cipher Mode| Key Length (Bit)| Padding Mode| API Version| 
  | -------- | -------- | -------- | -------- |
  | ECB | 192 | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | CBC | 192 | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | OFB | 192 | [NoPadding\|PKCS5\|PKCS7] | 9+ | 
  | CFB | 192 | [NoPadding\|PKCS5\|PKCS7] | 9+ | 

- Since API version 10, symmetric encryption and decryption support the algorithm specifications without the key length. If the symmetric key type does not contain the key length, the encryption and decryption operations vary with the actual key length.
  For example, if the block mode is CFB and the padding mode is **NoPadding** for a 3DES key with key length not specified, the string parameter is **3DES|CFB|NoPadding**.

## SM4

The Crypto framework provides the following cipher modes for [SM4](crypto-sym-key-generation-conversion-spec.md#sm4) encryption and decryption: ECB, CBC, CTR, OFB, CFB, CFB128, and GCM. The encryption and decryption parameters vary depending on the cipher mode. For details, see [ParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#paramsspec).

SM4 is a block cipher, with a fixed block size of 128 bits. If the last block is less than 128 bits (16 bytes), you can specify the [padding mode](#padding-mode) to pad data.

Because the data is padded to the block size, **PKCS5** and **PKCS7** used in the Crypto framework use the block size as the padding length. That is, data is padded to 16 bytes for SM4 encryption.

> **NOTE**
>
> In ECB and CBC modes, the plaintext must be padded if its length is not an integer multiple of 128 bits.

The SM4 encryption and decryption can be implemented based a string parameter. When creating a **Cipher** instance, you need to specify the algorithm specifications in a string parameter. The string parameter consists of the symmetric key type (algorithm_key length), cipher block mode, and padding mode with a vertical bar (|) in between.

- In the following table, the options included in the square brackets ([]) are mutually exclusive. You can use only one of them in a string parameter. The SM4 algorithm and key length are separated by an underscore (_).
  
  Example:
  - If the cipher block mode is ECB and padding mode is **PKCS7** for a 128-bit SM4 key, the string parameter is **SM4_128|ECB|PKCS7**.
  
  - If the cipher block mode is CFB and padding mode is **NoPadding** for a 128-bit SM4 key, the string parameter is **SM4_128|CFB|NoPadding**.

  - If the cipher block mode is GCM and padding mode is **NoPadding** for a 128-bit SM4 key, the string parameter is **SM4_128|GCM|NoPadding**.

  | Cipher Mode| Key Length (Bit)| Padding Mode| API Version| 
  | -------- | -------- | -------- | -------- |
  | ECB | 128 | [NoPadding\|PKCS5\|PKCS7] | 10+ | 
  | CBC | 128 | [NoPadding\|PKCS5\|PKCS7] | 10+ | 
  | CTR | 128 | [NoPadding\|PKCS5\|PKCS7] | 10+ | 
  | OFB | 128 | [NoPadding\|PKCS5\|PKCS7] | 10+ | 
  | CFB | 128 | [NoPadding\|PKCS5\|PKCS7] | 10+ | 
  | CFB128 | 128 | [NoPadding\|PKCS5\|PKCS7] | 10+ | 
  | GCM | 128 | [NoPadding\|PKCS5\|PKCS7] | 12+ | 

## Padding Mode

The block cipher algorithm has a fixed block length. If the length of the last block does not meet the requirement, data will be added to extend the block to the required length based on the padding mode. The following padding modes are supported:

- **NoPadding**: no padding. The length of the input data must match the block length.

- **PKCS5**: pads a block cipher with a block size of 8 bytes. PKCS#5 applies padding in whole bytes. The value of each added byte is the number of bytes that are added.

- **PKCS7**: pads a block cipher with a block size from 1 to 255 bytes. The padding scheme is the same as that of PKCS#5. PKCS#5 is defined for 8-byte block sizes, while PKCS#7 can work with block size ranging from 1 to 255 bytes.

For the modes that convert block ciphers into stream ciphers, such as CFB, OFB, CTR, GCM, and CCM, padding is not required. Therefore, **NoPadding** is used no matter whether the padding mode is specified.
