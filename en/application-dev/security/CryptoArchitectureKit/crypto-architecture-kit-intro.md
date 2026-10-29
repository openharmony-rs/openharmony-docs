# About This Kit

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=64044667f2ece520228c37a4e282d90b2e014ba4 translatedAt=2026-10-09T01:35:52.058Z pushedAt=2026-10-10T01:45:53.524Z -->

Crypto Architecture Kit provides cryptographic functionalities, such as encryption and decryption, signing and signature verification, message authentication code (MAC) generation, hash computation, random number generation, and key derivation.

By calling the cryptographic algorithm framework service, you can ignore the differences between underlying third-party cryptographic algorithm libraries and achieve rapid development.

## Constraints

- Crypto Architecture Kit does not support multi-thread concurrent operations.

- Crypto Architecture Kit is currently implemented based on OpenSSL.

- Crypto Architecture Kit provides most of the common algorithms. However, some algorithms and specifications, such as MD5, are not applicable to scenarios with high security requirements. Use appropriate algorithms based on service requirements.

## Capability Scope

Crypto Architecture Kit provides the following functionalities, with algorithm specifications and development guides for your reference.

- [Key Generation and Conversion](crypto-key-generation-conversion.md)

- [Introduction to Encryption and Decryption](crypto-encryption-decryption.md)

- [Signing and Signature Verification](crypto-sign-sig-verify-overview.md)

- [Key Agreement](crypto-key-agreement-overview.md)

- [MD](crypto-generate-message-digest-overview.md)

- [MAC](crypto-compute-mac-overview.md)

- [Random Number Generation](crypto-generate-random-number.md)

- [Key Derivation](crypto-key-derivation-overview.md)

## Basic Concepts

Before you get started, be sure to understand the following basic concepts:

- Symmetric key

  A symmetric key is a key used both to encrypt and decrypt data. In symmetric encryption, the sender converts information in plaintext into ciphertext using a key and certain algorithm for security purposes. The receiver converts the ciphertext into plaintext using the same key and algorithm.

- Asymmetric key

  In the asymmetric cryptography, a private and public key pair is required. The private key is used to encrypt the plaintext, and the public key is used to decrypt the ciphertext.

  The public key is public and open to anyone in the system, while the private key is private.

  For signing and signature verification, the private key is used to sign the plaintext, and the public key is used to verify the signature.

<!--RP1--><!--RP1End-->

## Related Kits

Crypto Architecture Kit provides cryptographic operations, but not key management. Therefore, applications must manage their own keys. This kit is applicable to scenarios where keys are used only in memory, such as temporary session keys, or where keys are securely stored by applications.

If key management (such as key storage) is required, use [Universal Keystore Kit](../UniversalKeystoreKit/huks-overview.md).
