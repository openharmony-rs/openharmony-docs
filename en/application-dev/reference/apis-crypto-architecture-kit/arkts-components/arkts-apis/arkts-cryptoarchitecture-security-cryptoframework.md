# @ohos.security.cryptoFramework(Crypto Framework)

The **cryptoFramework** module provides APIs for cryptographic operations, shielding the underlying hardware and algorithm library.

**Since:** 9

**Model restriction:** 
- API version 12 and later: This API can be used in both the stage model and FA model.
- API versions 9 to 11: This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createasykeygenerator-f.md) | Creates an **AsyKeyGenerator** instance based on the specified algorithm. |
| [createAsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) | Creates an **AsyKeyGeneratorBySpec** instance based on the specified key specifications. |
| [createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md) | Creates a **Cipher** instance. |
| [createKdf](arkts-cryptoarchitecture-cryptoframework-createkdf-f.md) | Creates a key derivation function instance. |
| [createKem](arkts-cryptoarchitecture-cryptoframework-createkem-f.md) | Creates a Kem instance for key encapsulation and decapsulation operations. |
| [createKeyAgreement](arkts-cryptoarchitecture-cryptoframework-createkeyagreement-f.md) | Creates a **KeyAgreement** instance. |
| [createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md) | Creates a **Mac** instance. |
| [createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md) | Creates a **Mac** instance. |
| [createMd](arkts-cryptoarchitecture-cryptoframework-createmd-f.md) | Creates an **Md** instance. |
| [createRandom](arkts-cryptoarchitecture-cryptoframework-createrandom-f.md) | Creates a **Random** instance. |
| [createSign](arkts-cryptoarchitecture-cryptoframework-createsign-f.md) | Creates a **Sign** instance. |
| [createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md) | Creates a symmetric key generator instance with the specified algorithm. |
| [createVerify](arkts-cryptoarchitecture-cryptoframework-createverify-f.md) | Creates a **Verify** instance. |

### Classes

| Name | Description |
| --- | --- |
| [DHKeyUtil](arkts-cryptoarchitecture-cryptoframework-dhkeyutil-c.md) | Generates common parameters for a DH key based on the prime **p** length and the private key length. |
| [ECCKeyUtil](arkts-cryptoarchitecture-cryptoframework-ecckeyutil-c.md) | Provides utilities for ECC key parameter generation and point conversion based on the specified elliptic curve. |
| [SignatureUtils](arkts-cryptoarchitecture-cryptoframework-signatureutils-c.md) | Provides utilities for converting ECC/SM2 signature data. |
| [SM2CryptoUtil](arkts-cryptoarchitecture-cryptoframework-sm2cryptoutil-c.md) | Provides APIs for SM2 cryptographic operations. |

### Interfaces

| Name | Description |
| --- | --- |
| [AeadParamsSpec](arkts-cryptoarchitecture-cryptoframework-aeadparamsspec-i.md) | Describes parameters in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption and decryption using authenticated encryption with associated data (AEAD). It inherits from [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md). |
| [AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md) | Asymmetric key generator interface, defining methods for generating asymmetric keys. Before use, you must create an **AsyKeyGenerator** instance by using [createAsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createasykeygenerator-f.md). |
| [AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md) | Asymmetric key generator interface with specified key specifications, defining methods for generating asymmetric keys based on specified key specifications. Before use, you must create an **AsyKeyGeneratorBySpec** instance by using [createAsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md). |
| [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) | Defines the asymmetric key parameters for creating a key generator. You need to construct a child class object and pass it to [createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md) to create a key generator. When constructing a child class object, use little-endian format for RSA keys and use big-endian format and positive numbers for other key parameters of the bigint type. |
| [CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md) | Encapsulates the parameters for encryption or decryption using the CCM AEAD mode, which requires an IV, AAD, and an authentication tag. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption. |
| [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) | Encryption and decryption interface, defining methods for symmetric and asymmetric encryption and decryption. Before use, you must create a **Cipher** instance by using [createCipher(transformation: string): Cipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md). Call the [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init), [update()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#update), and [doFinal()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#dofinal) APIs in this class as needed to complete encryption or decryption operations. |
| [CmacSpec](arkts-cryptoarchitecture-cryptoframework-cmacspec-i.md) | Represents the child class of [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md). It is used as an input parameter for CMAC computation. |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Encapsulates binary data. The core field **data** is of the Uint8Array type. |
| [DHCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dhcommonparamsspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the common parameters of the public and private keys in the DH algorithm. |
| [DHKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-dhkeypairspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the DH algorithm. |
| [DHPriKeySpec](arkts-cryptoarchitecture-cryptoframework-dhprikeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the private key in the DH algorithm. |
| [DHPubKeySpec](arkts-cryptoarchitecture-cryptoframework-dhpubkeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the DH algorithm. |
| [DSACommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-dsacommonparamsspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the common parameters of the public and private keys in the DSA algorithm. It can be used to randomly generate a public or private key. |
| [DSAKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-dsakeypairspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the DSA algorithm. |
| [DSAPubKeySpec](arkts-cryptoarchitecture-cryptoframework-dsapubkeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the DSA algorithm. |
| [ECCCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-ecccommonparamsspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the common parameters of the public and private keys in the ECC algorithm. It can be used to randomly generate a public or private key. |
| [ECCKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-ecckeypairspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the ECC algorithm. |
| [ECCPriKeySpec](arkts-cryptoarchitecture-cryptoframework-eccprikeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the private key in the ECC algorithm. |
| [ECCPubKeySpec](arkts-cryptoarchitecture-cryptoframework-eccpubkeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the ECC algorithm. |
| [EccSignatureSpec](arkts-cryptoarchitecture-cryptoframework-eccsignaturespec-i.md) | Represents the ECC/SM2 signature data that contains (r, s). |
| [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md) | Defines the field type of an elliptic curve. Currently, only the **Fp** field is supported. |
| [ECFieldFp](arkts-cryptoarchitecture-cryptoframework-ecfieldfp-i.md) | Defines the prime field of the elliptic curve. It is a child class of [ECField](arkts-cryptoarchitecture-cryptoframework-ecfield-i.md). |
| [ED25519KeyPairSpec](arkts-cryptoarchitecture-cryptoframework-ed25519keypairspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the Ed25519 algorithm. |
| [ED25519PriKeySpec](arkts-cryptoarchitecture-cryptoframework-ed25519prikeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the private key in the Ed25519 algorithm. |
| [ED25519PubKeySpec](arkts-cryptoarchitecture-cryptoframework-ed25519pubkeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the Ed25519 algorithm. |
| [GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md) | Encapsulates the parameters for encryption or decryption using the GCM AEAD mode, which requires an IV, AAD, and an authentication tag. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption. |
| [HKDFSpec](arkts-cryptoarchitecture-cryptoframework-hkdfspec-i.md) | Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is a parameter for HKDF key derivation. |
| [HmacSpec](arkts-cryptoarchitecture-cryptoframework-hmacspec-i.md) | Represents the child class of [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md). It is used as an input parameter for HMAC computation. |
| [IvParamsSpec](arkts-cryptoarchitecture-cryptoframework-ivparamsspec-i.md) | Encapsulates the parameters for encryption or decryption using a block cipher mode that requires an IV. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption. |
| [Kdf](arkts-cryptoarchitecture-cryptoframework-kdf-i.md) | Key derivation function (KDF) interface, defining methods for deriving keys based on key derivation parameters. Before use, you must create a **Kdf** instance by using [createKdf](arkts-cryptoarchitecture-cryptoframework-createkdf-f.md). |
| [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | Defines the parameters of the key derivation function. When the key derivation function is used to derive a key, you need to construct and pass in a child class object of **KdfSpec**. |
| [Kem](arkts-cryptoarchitecture-cryptoframework-kem-i.md) | Key encapsulation mechanism (KEM) interface, defining methods for key encapsulation and decapsulation based on KEM. Before use, you must create a **Kem** instance by using [createKem(algNameId: KemAlgNameId): Kem](arkts-cryptoarchitecture-cryptoframework-createkem-f.md). |
| [KemEncapResult](arkts-cryptoarchitecture-cryptoframework-kemencapresult-i.md) | Represents the encapsulation result of the KEM. |
| [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | Provides APIs for key operations. Before performing cryptographic operations (such as encryption and decryption), you need to construct a child class object of **Key** and pass it to [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) of the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance. |
| [KeyAgreement](arkts-cryptoarchitecture-cryptoframework-keyagreement-i.md) | Key agreement interface, defining methods for generating shared secrets based on asymmetric key pairs. Before use, you must create a **KeyAgreement** instance by using [createKeyAgreement(algName: string): KeyAgreement](arkts-cryptoarchitecture-cryptoframework-createkeyagreement-f.md). |
| [KeyEncodingConfig](arkts-cryptoarchitecture-cryptoframework-keyencodingconfig-i.md) | Represents the RSA private key encoding parameters. You can use it to generate an encoded private key string with the specified algorithm and password. |
| [KeyPair](arkts-cryptoarchitecture-cryptoframework-keypair-i.md) | Defines an asymmetric key pair, which includes a public key and a private key. |
| [Mac](arkts-cryptoarchitecture-cryptoframework-mac-i.md) | Message authentication code (MAC) interface, defining methods for calculating MACs based on symmetric keys. Before use, you must create a **Mac** instance by using [createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md). |
| [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md) | Represents the message authentication code (MAC) parameters. You need to construct a child class object and use it as a parameter when computing an HMAC or a CMAC. |
| [Md](arkts-cryptoarchitecture-cryptoframework-md-i.md) | Message digest interface, defining methods for calculating message digests. Before use, you must create an **Md** instance by using [createMd](arkts-cryptoarchitecture-cryptoframework-createmd-f.md). |
| [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) | Encapsulates the parameters used for encryption or decryption. You need to construct its child class object and pass it to [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption. |
| [PBKDF2Spec](arkts-cryptoarchitecture-cryptoframework-pbkdf2spec-i.md) | Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is used as a parameter for PBKDF2 key derivation. |
| [Point](arkts-cryptoarchitecture-cryptoframework-point-i.md) | Defines a point on the elliptic curve. |
| [Poly1305ParamsSpec](arkts-cryptoarchitecture-cryptoframework-poly1305paramsspec-i.md) | Encapsulates the parameters for encryption or decryption using the ChaCha20-Poly1305 AEAD mode, which requires a nonce, AAD, and an authentication tag. It is a child class of [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) and used as a parameter in [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) for symmetric encryption or decryption. |
| [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | Provides APIs for private key operations. **PriKey** is a child class of [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md). It needs to be passed in during asymmetric decryption, signing, and key agreement. |
| [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | Provides APIs for public key operations. **PubKey** is a child class of [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md). It needs to be passed in during asymmetric encryption, signature verification, and key agreement. |
| [Random](arkts-cryptoarchitecture-cryptoframework-random-i.md) | Random interface, defining methods for generating random numbers. Before use, you must create a **Random** instance by using [createRandom](arkts-cryptoarchitecture-cryptoframework-createrandom-f.md). |
| [RSACommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-rsacommonparamsspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the common parameters of the public and private keys in the RSA algorithm. It can be used to randomly generate a public or private key. |
| [RSAKeyPairSpec](arkts-cryptoarchitecture-cryptoframework-rsakeypairspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the RSA algorithm. |
| [RSAPubKeySpec](arkts-cryptoarchitecture-cryptoframework-rsapubkeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the RSA algorithm. |
| [ScryptSpec](arkts-cryptoarchitecture-cryptoframework-scryptspec-i.md) | Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is a parameter for scrypt key derivation function (KDF). |
| [Sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md) | Signing interface, defining methods for signing data using a private key. Before use, you must create a **Sign** instance by using [createSign(algName: string): Sign](arkts-cryptoarchitecture-cryptoframework-createsign-f.md). Invoke **init()**, **update()**, and **sign()** in this class in sequence to complete the signing operation. For details about the sample code, see [Signing and Signature Verification with an RSA Key Pair (PKCS1 Mode)](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md). |
| [SM2CipherTextSpec](arkts-cryptoarchitecture-cryptoframework-sm2ciphertextspec-i.md) | Represents the SM2 ciphertext parameters. You can use this object to generate SM2 ciphertext in ASN.1 format or obtain SM2 parameters from the SM2 ciphertext in ASN.1 format. |
| [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | Provides APIs for symmetric key operations. It is a child class of [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md). Its objects need to be passed to [init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init) of the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance in symmetric encryption and decryption. |
| [SymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md) | Symmetric key generator interface, defining methods for generating symmetric keys. Before use, you must create a **SymKeyGenerator** instance by using [createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md). |
| [Verify](arkts-cryptoarchitecture-cryptoframework-verify-i.md) | Signature verification interface, defining methods for verifying signatures using a public key. Before use, you must create a **Verify** instance by using [createVerify(algName: string): Verify](arkts-cryptoarchitecture-cryptoframework-createverify-f.md). Invoke **init()**, **update()**, and **verify()** in this class in sequence to complete the signature verification. For details about the sample code, see [Signing and Signature Verification with an RSA Key Pair (PKCS1 Mode)](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md). |
| [X25519KeyPairSpec](arkts-cryptoarchitecture-cryptoframework-x25519keypairspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify full parameters of the public and private keys in the X25519 algorithm. |
| [X25519PriKeySpec](arkts-cryptoarchitecture-cryptoframework-x25519prikeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the private key in the X25519 algorithm. |
| [X25519PubKeySpec](arkts-cryptoarchitecture-cryptoframework-x25519pubkeyspec-i.md) | Defines a child class of [AsyKeySpec](arkts-cryptoarchitecture-cryptoframework-asykeyspec-i.md) used to specify the parameters of the public key in the X25519 algorithm. |
| [X963KdfSpec](arkts-cryptoarchitecture-cryptoframework-x963kdfspec-i.md) | Defines the child class of [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md). It is a parameter for X963KDF key derivation function (KDF). |

### Enums

| Name | Description |
| --- | --- |
| [AsyKeyDataItem](arkts-cryptoarchitecture-cryptoframework-asykeydataitem-e.md) | Enumerates the asymmetric key data types. |
| [AsyKeySpecItem](arkts-cryptoarchitecture-cryptoframework-asykeyspecitem-e.md) | Enumerates the asymmetric key parameters. |
| [AsyKeySpecType](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md) | Enumerates the key parameter types. |
| [CipherSpecItem](arkts-cryptoarchitecture-cryptoframework-cipherspecitem-e.md) | Enumerates encryption and decryption parameters, which can be set by using [setCipherSpec](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#setcipherspec) and obtained by using [getCipherSpec](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#getcipherspec). |
| [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | Enumerates cipher operation modes for encryption and decryption. |
| [KemAlgNameId](arkts-cryptoarchitecture-cryptoframework-kemalgnameid-e.md) | Enumerates the KEM algorithm name IDs. |
| [Result](arkts-cryptoarchitecture-cryptoframework-result-e.md) | Enumerates the operation results. |
| [SignSpecItem](arkts-cryptoarchitecture-cryptoframework-signspecitem-e.md) | Enumerates the signing and signature verification parameters, which can be set by using [setSignSpec](arkts-cryptoarchitecture-cryptoframework-sign-i.md#setsignspec) and [setVerifySpec](arkts-cryptoarchitecture-cryptoframework-verify-i.md#setverifyspec), and obtained by using [getSignSpec](arkts-cryptoarchitecture-cryptoframework-sign-i.md#getsignspec) and [getVerifySpec](arkts-cryptoarchitecture-cryptoframework-verify-i.md#getverifyspec). |
