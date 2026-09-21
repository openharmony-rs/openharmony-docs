# Key Generation and Conversion

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=9e4c590f961177b8a61618e6103f3c92cc5e6e52 translatedAt=2026-09-03T08:55:48.667Z pushedAt=2026-09-03T09:48:11.341Z -->

Key generation is often required in the following scenarios:

1. Randomly generate a key object of the algorithm library. The object can be used for subsequent operations such as encryption and decryption.

2. Generate a key object of the algorithm library based on specified data (that is, convert binary data obtained from an external source or storage system into a key object of the algorithm library). The object can be used for subsequent operations such as encryption and decryption.

3. Generate a specified key object of the algorithm library based on key parameters. The object can be used for subsequent operations such as encryption and decryption.

4. Obtain the binary data of the key object of the algorithm library for storage or transmission.

5. For asymmetric keys, obtain the parameter attributes of the key object for storage or transmission.

The key object Key includes the symmetric key SymKey and the asymmetric key (public key PubKey and private key PriKey), where the public key and private key form a key pair KeyPair.

## Symmetric Key Generation and Conversion Specifications

This section describes the algorithms currently supported by the system and their corresponding specifications.

Developers can carry key specifications as string parameters to generate the corresponding keys. The string parameters supported for each algorithm will be introduced in the specific specifications of each algorithm.

### AES

AES (Advanced Encryption Standard) is the most common symmetric encryption algorithm.

Basic characteristics:

- A block cipher algorithm with a block length of 128 bits.

- The key length is 128 bits, 192 bits, or 256 bits.

- Compared with 3DES, it offers higher security and faster processing speed.

Currently supported is the generation of AES keys using a string parameter. The specific "string parameter" is concatenated from the "symmetric key algorithm" and the "key length", and is used to specify the key specification when creating a symmetric key generator.

| Symmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| AES | 128 | AES128 | 9+ | 
| AES | 192 | AES192 | 9+ | 
| AES | 256 | AES256 | 9+ | 

### DES
DES (Data Encryption Standard) algorithm.

Basic characteristics:

DES is a block cipher that divides plaintext into 64-bit blocks and then encrypts each block.

Currently supported is the generation of a DES key using a string parameter. The specific "string parameter" is concatenated from the "symmetric key algorithm" and the "key length", and is used to specify the key specification when creating a symmetric key generator.

| Symmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| DES | 64 | DES64 | 20+ | 

### 3DES

3DES (Triple Data Encryption Algorithm), also known as 3DESede or TripleDES.

Basic characteristics:

- Uses three 64-bit keys to encrypt a data block three times, which is equivalent to performing the DES (Data Encryption Standard) encryption algorithm three times on each data block.

- Compared with DES, 3DES has a longer key length and higher security, but its processing speed is lower than that of DES.

Currently supported is the generation of 3DES keys using a string parameter. The specific "string parameter" is concatenated from the "symmetric key algorithm" and the "key length", and is used to specify the key specifications when creating a symmetric key generator.

| Symmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| 3DES | 192 | 3DES192 | 9+ | 

### SM4

SM4, namely the SM4 block cipher algorithm.

Basic characteristics:

- Block cipher algorithm with a block length of 128 bits.

- The key length is 128 bits. It can be extended by expanding the key.

- Both the encryption algorithm and the key expansion algorithm adopt a 32-round nonlinear iterative structure. The data decryption and data encryption algorithms share the same structure, except that the round keys are used in reverse order; the decryption round keys are the reverse of the encryption round keys.

Currently supported is the generation of SM4 keys using a string parameter. The specific "string parameter" is formed by concatenating the "symmetric key algorithm" and the "key length" with the connector "_", and is used to specify the key specification when creating a symmetric key generator.

| Symmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| SM4 | 128 | SM4_128 | 10+ | 

### HMAC

HMAC (Hash-based message authentication code) is a hash-based message authentication code algorithm that requires a symmetric key as input during computation.

Basic characteristics:

The symmetric key used by HMAC can be of any length.

- If the key length is greater than the HMAC block length, the result of applying a one-way hash to the key is used as the new key.

- If the key length is less than the HMAC block length, zeros are padded to the end as the new key, so that the final key length is consistent with the HMAC block length.

- It is recommended that the key length be the output length of the digest algorithm.

Currently, symmetric keys for HMAC can be generated using a string parameter in the following two ways:

- When the key length used by HMAC is the same as the output length of the digest algorithm, the specific "string parameter" is concatenated from the "message authentication code algorithm" and the "digest algorithm" using the connector "|", and is used to specify the key specification when creating a symmetric key generator.

- When the key length used by HMAC is not within the range of the output length of the digest algorithms mentioned above, a symmetric key generator can be created through the string parameter "HMAC", and the key is generated based on the binary data of the key used by HMAC.

| Message Authentication Code Algorithm | Digest Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- | -------- |
| HMAC | SHA1 | 160 | HMAC\|SHA1 | 11+ | 
| HMAC | SHA224 | 224 | HMAC\|SHA224 | 11+ | 
| HMAC | SHA256 | 256 | HMAC\|SHA256 | 11+ | 
| HMAC | SHA384 | 384 | HMAC\|SHA384 | 11+ | 
| HMAC | SHA512 | 512 | HMAC\|SHA512 | 11+ | 
| HMAC | SM3 | 256 | HMAC\|SM3 | 11+ | 
| HMAC | - | [1, 32768] | HMAC | 11+ | 

### ChaCha20

Starting from API version 22, the algorithm library supports this algorithm.

ChaCha20 is a modern stream cipher symmetric encryption algorithm.

Basic characteristics:

- It is a stream cipher algorithm and does not require a padding algorithm.

- The key length is 256 bits.

| Symmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| ChaCha20 | 256 | ChaCha20 | 22+ | 

### RC2
Starting from API version 26.0.0, the algorithm library supports this algorithm.

RC2 is a block cipher with a block length of 64 bits.

Basic characteristics:

- The block length is 64 bits (8 bytes).
- The supported key length ranges from 8 to 1024 bits, and the string parameter is RC2.

| Symmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| RC2 | 8 to 1024 | RC2 | 26.0.0+ | 

### RC4
Starting from API version 26.0.0, the algorithm library supports this algorithm.

RC4 is a stream cipher algorithm.

Basic characteristics:

- Stream cipher, no padding required.
- The key length ranges from 8 to 4096 bits, and the string parameter is RC4.

| symmetric key algorithm | key length (bit) | string parameter | API version | 
| -------- | -------- | -------- | -------- |
| RC4 | 8-4096 | RC4 | 26.0.0+ | 

### Blowfish (BF)
Starting from API version 26.0.0, the algorithm library supports this algorithm.

Blowfish is a block cipher algorithm with a block length of 64 bits.

Basic characteristics:

- The block length is 64 bits (8 bytes).
- The key length supports 32 to 448 bits, and the string parameter is Blowfish.

| Symmetric key algorithm | Key length (bit) | String parameter | API version | 
| -------- | -------- | -------- | -------- |
| Blowfish | 32 to 448 | Blowfish | 26.0.0+ |

### CAST
Starting from API version 26.0.0, the algorithm library supports this algorithm.

CAST (such as CAST-128/CAST5) is a block cipher algorithm with a block length of 64 bits.

Basic characteristics:

- The block length is 64 bits (8 bytes).
- The key length ranges from 40 bits to 128 bits, and the string parameter is CAST.

| Symmetric key algorithm | Key length (bit) | String parameter | API version | 
| -------- | -------- | -------- | -------- |
| CAST | 40-128 | CAST | 26.0.0+ |

## Asymmetric Key Generation and Conversion Specifications

This section describes the algorithms supported by the system and their corresponding specifications. There are two ways to specify the specifications for key generation:

- String parameter: describes the key specifications that developers need to generate in the form of a string.

- Key parameters: uses the detailed cryptographic information of the key to construct a key object.

Which method is used for each algorithm will be introduced in the specifications of each algorithm.

### RSA

RSA (Rivest–Shamir–Adleman) currently supports key generation using both string parameters and key parameters.

**Generation Using String Parameters**

To generate an RSA key using string parameters, the specific "string parameter" is formed by concatenating the "RSA key type" and the "number of primes" with the symbol "|". It is used to specify the key specifications when creating an asymmetric key generator.

> **Note:**
>
> When generating an RSA asymmetric key, the default number of primes is 2, and the PRIMES_2 parameter can be omitted.

| RSA Key Type | Number of Primes | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| RSA512 | 2 | RSA512\|PRIMES_2 | 9+ | 
| RSA768 | 2 | RSA768\|PRIMES_2 | 9+ | 
| RSA1024 | 2 | RSA1024\|PRIMES_2 | 9+ | 
| RSA1024 | 3 | RSA1024\|PRIMES_3 | 9+ | 
| RSA2048 | 2 | RSA2048\|PRIMES_2 | 9+ | 
| RSA2048 | 3 | RSA2048\|PRIMES_3 | 9+ | 
| RSA3072 | 2 | RSA3072\|PRIMES_2 | 9+ | 
| RSA3072 | 3 | RSA3072\|PRIMES_3 | 9+ | 
| RSA4096 | 2 | RSA4096\|PRIMES_2 | 9+ | 
| RSA4096 | 3 | RSA4096\|PRIMES_3 | 9+ | 
| RSA4096 | 4 | RSA4096\|PRIMES_4 | 9+ | 
| RSA8192 | 2 | RSA8192\|PRIMES_2 | 9+ | 
| RSA8192 | 3 | RSA8192\|PRIMES_3 | 9+ | 
| RSA8192 | 4 | RSA8192\|PRIMES_4 | 9+ | 
| RSA8192 | 5 | RSA8192\|PRIMES_5 | 9+ | 

> **Caution:**
>
> Using synchronous APIs to generate RSA2048, RSA3072, RSA4096, and RSA8192 asymmetric keys increases the time consumed.
>
> The system imposes a time limit on the main thread, and time-consuming operations may fail. When generating large-size keys, you are advised to use asynchronous APIs or [use multi-threaded concurrency](../../arkts-utils/multi-thread-concurrency-overview.md).
>
> When creating an RSA asymmetric key generator, if it is used for random key generation, the generated RSA key specifications are consistent with the key specifications specified at creation; if it is used for key conversion, the generated RSA key specifications are consistent with the key data specifications specified during conversion.

**Generation Using Key Parameters**

Starting from API version 10, RSA keys can be generated using key parameters.

RSA key parameters involve three integers, including:

- n: modulus, a common parameter of the private key and public key.

- sk: private exponent, often written as d in formulas.

- pk: public exponent, often written as e in formulas.

When creating an asymmetric key generator, RSA keys can be generated based on the specified public and private key parameters. For details, see the following table:

- √: indicates that the specific attribute in this column must be specified to form the key parameters.

- ×: indicates that the specific attribute in this column corresponds to a certain type of key parameters, but generating a key from these key parameters is currently not supported.

| Parameter Name | Common Parameters | Public Key Parameters | Private Key Parameters | Public-Private Key Pair Parameters | 
| -------- | -------- | -------- | -------- | -------- |
| n | × | √ | × | √ | 
| pk | N/A | √ | N/A | √ | 
| sk | N/A | N/A | × | √ |

Based on the table above:

- RSA does not support random generation of keys by specifying the common parameter (n).

- RSA does not support generating a private key by specifying the private key parameters (n, sk).

### ECC

ECC (Elliptic Curve Cryptography) is a public-key cryptographic algorithm based on elliptic curve mathematics.

Elliptic curve algorithms can be regarded as operations on numbers defined over special sets. All ECC keys supported by the current algorithm library are elliptic curves over the Fp field, where p is a prime number. The Fp field is also called a prime field.

ECC keys can be generated using string parameters and key parameters. Public key parameters can also be generated by curve name.

**Generation Using String Parameters**

To generate an ECC key using string parameters, the specific "string parameter" is concatenated from the "asymmetric key algorithm" and the "key length", and is used to specify the key specification when creating an asymmetric key generator.

| Asymmetric Key Algorithm | Key Length (bit) | Curve Name | String Parameter | API Version | 
| -------- | -------- | -------- | -------- | -------- |
| ECC | 192 | NID_X9_62_prime192v1 | ECC192 | 26.0.0+ | 
| ECC | 224 | NID_secp224r1 | ECC224 | 9+ | 
| ECC | 256 | NID_X9_62_prime256v1 | ECC256 | 9+ | 
| ECC | 384 | NID_secp384r1 | ECC384 | 9+ | 
| ECC | 521 | NID_secp521r1 | ECC521 | 9+ | 
| ECC | 160 | NID_brainpoolP160r1 | ECC_BrainPoolP160r1 | 11+ | 
| ECC | 160 | NID_brainpoolP160t1 | ECC_BrainPoolP160t1 | 11+ | 
| ECC | 192 | NID_brainpoolP192r1 | ECC_BrainPoolP192r1 | 11+ | 
| ECC | 192 | NID_brainpoolP192t1 | ECC_BrainPoolP192t1 | 11+ | 
| ECC | 224 | NID_brainpoolP224r1 | ECC_BrainPoolP224r1 | 11+ | 
| ECC | 224 | NID_brainpoolP224t1 | ECC_BrainPoolP224t1 | 11+ | 
| ECC | 256 | NID_brainpoolP256r1 | ECC_BrainPoolP256r1 | 11+ | 
| ECC | 256 | NID_brainpoolP256t1 | ECC_BrainPoolP256t1 | 11+ | 
| ECC | 320 | NID_brainpoolP320r1 | ECC_BrainPoolP320r1 | 11+ | 
| ECC | 320 | NID_brainpoolP320t1 | ECC_BrainPoolP320t1 | 11+ | 
| ECC | 384 | NID_brainpoolP384r1 | ECC_BrainPoolP384r1 | 11+ | 
| ECC | 384 | NID_brainpoolP384t1 | ECC_BrainPoolP384t1 | 11+ | 
| ECC | 512 | NID_brainpoolP512r1 | ECC_BrainPoolP512r1 | 11+ | 
| ECC | 512 | NID_brainpoolP512t1 | ECC_BrainPoolP512t1 | 11+ | 
| ECC | 256 | NID_secp256k1 | ECC_Secp256k1 | 14+ | 

> **Note:**
>
> When creating an ECC asymmetric key generator, if it is used for random key generation, the generated ECC key specification is consistent with the key specification specified when creating the key generator. If it is used for key conversion, the generated ECC key specification is consistent with the key data specification specified during key conversion.

**Generation Using Key Parameters**

Starting from API version 10, ECC keys can be generated using key parameters.

The ECC key parameters in the Fp field include:

- p: a prime number used to determine Fp.

- a, b: determine the equation of the elliptic curve.

- g: a base point on the elliptic curve, which can be represented by gx and gy.

- n: the order of the base point g.

- h: the cofactor.

- sk: the private key, which is a random integer less than n.

- pk: the public key, which is a point on the elliptic curve, pk = sk \* g.

When creating an asymmetric key generator, you can use the specified public and private key parameters to generate an ECC key. For details, see the following table:

- √: indicates that the specific attribute in this column must be specified to form the key parameters.

| Parameter Name | Common Parameter | Public Key Parameters | Private Key Parameters | Public-Private Key Pair Parameters |
| -------- | -------- | -------- | -------- | -------- |
| fieldType | √ | √ | √ | √ |
| p | √ | √ | √ | √ |
| a | √ | √ | √ | √ |
| b | √ | √ | √ | √ |
| g | √ | √ | √ | √ |
| n | √ | √ | √ | √ |
| h | √ | √ | √ | √ |
| pk | N/A | √ | N/A | √ |
| sk | N/A | N/A | √ | √ |

> **Note:**
>
> - Currently, ECC supports only the Fp field, so fieldType is fixed to "Fp". fieldType and p together form the field attribute, which currently supports only [ECFieldFp](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#ecfieldfp10).
>
> - g and pk are points on the ECC curve, of the [Point](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#point10) type, and require specifying the specific X and Y coordinates.

**Generating Key Parameters Using a Curve Name**

Starting from API version 11, a curve name can be used to generate ECC public key parameters.

> **Note:**
>
> - The curve name is a required string parameter. For supported curve names, see the "Curve Name" column in the ECC key string parameter table.
>
> - The generated public key parameters can be used directly for random generation of public-private key pairs, and can also be used to construct public key, private key, and public-private key pair key parameters.

### DSA

DSA (Digital Signature Algorithm) is a public-key cryptographic algorithm based on modular arithmetic and the discrete logarithm problem over integer finite fields. It is commonly used for digital signing and signature verification, and cannot be used for encryption or decryption.

Currently, DSA keys can be generated using either string parameters or key parameters.

**Constraints**

Using a synchronous API to generate DSA2048 or DSA3072 asymmetric keys, or processing plaintext longer than 2048 bits, increases the time consumed.

The system imposes a time limit on the main thread, and time-consuming operations may fail. When generating large-bit keys, you are advised to use an asynchronous API or [use multi-thread concurrency](../../arkts-utils/multi-thread-concurrency-overview.md).

**Use string parameters for generation**

To generate a DSA key using string parameters, the specific "string parameter" is concatenated from the "asymmetric key algorithm" and the "key length", and is used to specify the key specification when creating an asymmetric key generator.

| Asymmetric Key Algorithm | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- |
| DSA | 1024 | DSA1024 | 10+ | 
| DSA | 2048 | DSA2048 | 10+ | 
| DSA | 3072 | DSA3072 | 10+ | 

> **Note:**
>
> Using a synchronous API to generate DSA2048 or DSA3072 asymmetric keys, or processing plaintext longer than 2048 bits, increases the time consumed.
>
> The system imposes a time limit on the main thread, and time-consuming operations may fail. When generating large-bit keys, you are advised to use an asynchronous API or [use multi-thread concurrency](../../arkts-utils/multi-thread-concurrency-overview.md).
>
> When the created DSA asymmetric key generator is used for random key generation, the generated key specification is consistent with the key specification specified at creation. When it is used for key conversion, the generated key specification is consistent with the key data specification specified during conversion.

**Use key parameters for generation**

Supported since API version 10. DSA keys can be generated using key parameters.

DSA key parameters include:

- p: a prime modulus whose bit length is an integer multiple of 64.

- q: a prime factor of p-1, whose length is related to the length of p.

- g: g = (h ^ ((p - 1) / q)) mod p, where h is any integer satisfying 1 &lt; h &lt; p - 1.

- sk: the private key, a randomly generated integer satisfying 0 &lt; sk &lt; q.

- pk: the public key, pk = (g ^ sk) mod p.

When creating an asymmetric key generator, DSA keys can be generated based on the specified public and private key parameters. For details, see the following table:

- √: indicates that the specific attribute in this column must be specified to form the key parameters.

- ×: indicates that the specific attribute in this column corresponds to a certain key parameter, but key generation through this key parameter is not currently supported.

| Parameter Name | Common Parameter | Public Key Parameter | Private Key Parameter | Public-Private Key Pair Parameter | 
| -------- | -------- | -------- | -------- | -------- |
| p | √ | √ | × | √ | 
| q | √ | √ | × | √ | 
| g | √ | √ | × | √ | 
| pk | N/A | √ | N/A | √ | 
| sk | N/A | N/A | × | √ |

> **Note:**
>
> - DSA does not support generating a private key by specifying private key parameters (p, q, g, sk).
> 
> - When using common parameters (p, q, g) to generate a DSA key pair, the DSA key length must be at least 1024 bits.

### SM2

SM2 is a public-key cryptographic algorithm based on elliptic curves, using elliptic curves over the Fp field.

Currently supported are SM2 key generation using string parameters and key parameters, as well as generation of public key parameters by curve name.

**Generation using string parameters**

Currently supported is SM2 key generation using string parameters. The specific "string parameter" is formed by concatenating the "asymmetric key algorithm" and the "key length" with the symbol "_", and is used to specify the key specification when creating an asymmetric key generator.

| Asymmetric key algorithm | Key length (bit) | Curve name | String parameter | API version | 
| -------- | -------- | -------- | -------- | -------- |
| SM2 | 256 | NID_sm2 | SM2_256 | 10+ | 

**Generation using key parameters**

Starting from API version 11, SM2 key generation using key parameters is supported.

The SM2 key parameters over the Fp field include:

- p: a prime number used to determine Fp.

- a, b: Determine the equation of the elliptic curve.

- g: A base point on the elliptic curve, which can be represented by gx and gy.

- n: The order of the base point g.

- h: The cofactor.

- sk: The private key, which is a random integer less than n.

- pk: The public key, which is a point on the elliptic curve, pk = sk \* g.

When creating an asymmetric key generator, SM2 key generation based on the specified public key and private key parameters is supported. The specific support is shown in the following table:

- √: Indicates that the specific attribute in this column must be specified to form the key parameters.

| Parameter Name | Common Parameter | Public Key Parameters | Private Key Parameters | Public-Private Key Pair Parameters | 
| -------- | -------- | -------- | -------- | -------- |
| fieldType | √ | √ | √ | √ | 
| p | √ | √ | √ | √ | 
| a | √ | √ | √ | √ | 
| b | √ | √ | √ | √ | 
| g | √ | √ | √ | √ | 
| n | √ | √ | √ | √ | 
| h | √ | √ | √ | √ | 
| pk | N/A | √ | N/A | √ | 
| sk | N/A | N/A | √ | √ |

> **Note:**
>
> - Currently, SM2 supports only the Fp field, so fieldType is fixed to "Fp". fieldType and p form the field attribute, which currently supports only [ECFieldFp](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#ecfieldfp10).
> 
> - g and pk are points on the SM2 curve, of the [Point](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#point10) type, and their specific X and Y coordinates must be specified.

**Generating key parameters using a curve name**

Starting from API version 11, SM2 public key parameters can be generated using a curve name.

> **Note:**
>
> - The curve name is a required string parameter, and the supported curve name is "NID_sm2".
>
> - The generated public key parameters can be used directly for random generation of a public-private key pair, and can also be used to construct public key, private key, and public-private key pair parameters.

### Ed25519

The Ed25519 algorithm is a digital signature algorithm based on the EdDSA algorithm. It has a key length of 256 bits and is implemented using the Edwards curve. This algorithm does not support encryption or decryption and is mainly used for digital signing and verification.

Currently, Ed25519 key generation using string parameters and key parameters is supported.

**Generation Using String Parameters**

Generate an Ed25519 key using string parameters to specify the key specifications when creating an asymmetric key generator.

| Asymmetric Key Algorithm | String Parameter | API Version | 
| -------- | -------- | -------- |
| Ed25519 | Ed25519 | 11+ | 

**Generation Using Key Parameters**

Starting from API version 11, Ed25519 key generation using key parameters is supported.

Ed25519 key parameters include:

- sk: private key, a 32-byte random value.

- pk: public key, a 32-byte value derived from the private key.

When creating an asymmetric key generator, Ed25519 keys can be generated based on the specified public key and private key parameters. For details, see the following table:

- √: indicates that the specific attribute in this column must be specified to form the key parameters.

| Parameter Name | Public Key Parameters | Private Key Parameters | Public-Private Key Pair Parameters |
| -------- | -------- | -------- | -------- |
| pk | √ | N/A | √ |
| sk | N/A | √ | √ |

> **Note:**
>
> Ed25519 key parameters have no common parameters, and key generation through common parameters is not supported.

### X25519

The X25519 algorithm is a Diffie-Hellman key exchange algorithm used for key agreement.

It supports generating X25519 keys using string parameters and key parameters.

**Generation Using String Parameters**

Generate an X25519 key using string parameters and specify the key specifications.

| Asymmetric Key Algorithm | String Parameter | API Version | 
| -------- | -------- | -------- |
| X25519 | X25519 | 11+ | 

**Generation Using Key Parameters**

Starting from API version 11, generating X25519 keys using key parameters is supported.

X25519 key parameters include:

- sk: private key, a 32-byte random value.

- pk: public key, a 32-byte value derived from the private key.

When creating an asymmetric key generator, the support for generating X25519 keys by specifying public/private key parameters is shown in the following table.

- √: indicates that the specific attribute in this column must be specified to form the key parameters.

| Parameter Name | Public Key Parameters | Private Key Parameters | Public-Private Key Pair Parameters |
| -------- | -------- | -------- | -------- |
| pk | √ | N/A | √ |
| sk | N/A | √ | √ |

> **Note:**
>
> X25519 has no public key parameters and does not support key generation through public parameters.

### DH

DH (Diffie–Hellman key exchange) is a key agreement algorithm that involves only the exchange of public keys. It provides forward secrecy, meaning that even if the communication channel is monitored, the private keys of both parties are not exposed.

It supports generating DH keys using string parameters and key parameters, and supports generating public key parameters based on the prime length and private key length.

**Generation Using String Parameters**

To generate a DH key using string parameters, the specific "string parameter" is formed by concatenating the "asymmetric key algorithm" and the "well-known safe prime group parameter" with the symbol "_", and is used to specify the key specification when creating an asymmetric key generator.

| Asymmetric Key Algorithm | Well-known Safe Prime Group Parameter | Key Length (bit) | String Parameter | API Version | 
| -------- | -------- | -------- | -------- | -------- |
| DH | modp1536 | 1536 | DH_modp1536 | 11+ | 
| DH | modp2048 | 2048 | DH_modp2048 | 11+ | 
| DH | modp3072 | 3072 | DH_modp3072 | 11+ | 
| DH | modp4096 | 4096 | DH_modp4096 | 11+ | 
| DH | modp6144 | 6144 | DH_modp6144 | 11+ | 
| DH | modp8192 | 8192 | DH_modp8192 | 11+ | 
| DH | ffdhe2048 | 2048 | DH_ffdhe2048 | 11+ | 
| DH | ffdhe3072 | 3072 | DH_ffdhe3072 | 11+ | 
| DH | ffdhe4096 | 4096 | DH_ffdhe4096 | 11+ | 
| DH | ffdhe6144 | 6144 | DH_ffdhe6144 | 11+ | 
| DH | ffdhe8192 | 8192 | DH_ffdhe8192 | 11+ | 

> **Note:**
>
> When creating a DH asymmetric key generator, if it is used for random key generation, the generated DH key specification is consistent with the key specification specified when creating the key generator; if it is used for key conversion, the generated DH key specification is consistent with the key data specification specified during key conversion.

**Generation Using Key Parameters**

Starting from API version 11, generating DH keys using key parameters is supported.

DH key parameters include:

- p: A sufficiently large prime number used as the modulus of the finite field. It is shared by all communicating parties.

- g: g is the generator of the DH algorithm and the primitive root of the prime number p. It is shared by all communicating parties.

- l: length, indicating the private key length in bits. When l is 0, it means that the private key length is not specified.

- sk: private key, a randomly generated private key value.

- pk: public key, obtained by computation using the common parameters (p and g) and the private key.

When creating an asymmetric key generator, the support for generating DH keys with specified public/private key parameters is shown in the following table.

- √: indicates that the specific attribute in this column must be specified to form the key parameters.

| Parameter Name | Common Parameter | Public Key Parameters | Private Key Parameters | Public-Private Key Pair Parameters | 
| -------- | -------- | -------- | -------- | -------- |
| p | √ | √ | √ | √ | 
| g | √ | √ | √ | √ | 
| l | √ | √ | √ | √ | 
| pk | N/A | √ | N/A | √ | 
| sk | N/A | N/A | √ | √ |

**Generating public key parameters using prime length and private key length**

Starting from API version 11, DH public key parameters are generated using the prime length and private key length.

If the prime length is consistent with the prime length of a safe prime group, the corresponding well-known safe prime group is selected. The mapping is shown in the following table.

| Prime Length (bit) | Well-Known Safe Prime Group |
| -------- | -------- |
| 2048 | ffdhe2048 |
| 3072 | ffdhe3072 |
| 4096 | ffdhe4096 |
| 6144 | ffdhe6144 |
| 8192 | ffdhe8192 |

- The bit length of prime p must be greater than or equal to 512 and less than or equal to 10000.

- The private key length l is an optional parameter and defaults to 0. The value of l must be greater than 2*(96+(number of bits of prime p - 1)/1024*16).

- The generated public key parameters can be directly used for random generation of a public-private key pair, or for constructing a public key, a private key, or a public-private key pair.

- Generating key parameters for a non-well-known group is time-consuming. It is recommended to preferentially select a well-known safe prime group.

### ML-KEM

Starting from API version 26.0.0, the ML-KEM (Module-Lattice-Based Key-Encapsulation Mechanism) algorithm is supported. This algorithm is a post-quantum cryptographic algorithm based on a module-lattice key encapsulation mechanism.

Currently supported is the use of a string parameter for ML-KEM key generation.

**Use string parameter for generation**

Use a string parameter to generate an ML-KEM key, so as to specify the key specifications when creating an asymmetric key generator.

| Asymmetric key algorithm | Parameter set | String parameter | API version |
| -------- | -------- | -------- | -------- |
| ML-KEM | ML-KEM-512 | ML-KEM-512 |26.0.0+ |
| ML-KEM | ML-KEM-768 | ML-KEM-768 |26.0.0+ |
| ML-KEM | ML-KEM-1024 | ML-KEM-1024 |26.0.0+ |

### ML-DSA

Starting from API version 26.0.0, the Module-Lattice-Based Digital Signature Algorithm (ML-DSA) algorithm is supported. This algorithm is a post-quantum cryptographic digital signature algorithm based on module lattices.

Currently supported is the generation of ML-DSA keys using string parameters.

**Generation Using String Parameters**

Generate ML-DSA keys using string parameters to specify the key specifications when creating an asymmetric key generator.

| Asymmetric Key Algorithm | Parameter Set | String Parameter | API Version |
| -------- | -------- | -------- | -------- |
| ML-DSA | ML-DSA-44 | ML-DSA-44 |26.0.0+ |
| ML-DSA | ML-DSA-65 | ML-DSA-65 |26.0.0+ |
| ML-DSA | ML-DSA-87 | ML-DSA-87 |26.0.0+ |
