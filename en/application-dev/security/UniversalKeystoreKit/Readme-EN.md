# Universal Keystore Kit (Key Management Service)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

- [Introduction to Universal Keystore Kit](huks-overview.md)
- [Basic Concepts of HUKS](huks-concepts.md)
- Key Generation and Import<!--huks-key-generation-import-->
  - Key Generation<!--huks-key-generation-->
    - [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md)
    - Development<!--huks-key-generation-dev-->
      - [Generating a Key (ArkTS)](huks-key-generation-arkts.md)
      - [Generating a Key (C/C++)](huks-key-generation-ndk.md)
  - Key Import<!--huks-key-import-->
    - [Key Import Overview and Algorithm Specifications](huks-key-import-overview.md)
    - Development<!--huks-key-import-dev-->
      - [Importing a Key in Plaintext (ArkTS)](huks-import-key-in-plaintext-arkts.md)
      - [Importing a Key in Plaintext (C/C++)](huks-import-key-in-plaintext-ndk.md)
      - [Importing a Key in Ciphertext (ArkTS)](huks-import-wrapped-key-arkts.md)
      - [Importing a Key in Ciphertext (C/C++)](huks-import-wrapped-key-ndk.md)
- Key Use<!--huks-key-use-->
  - [General Process of Using a Key](huks-key-use-overview.md)
  - Encryption and Decryption<!--huks-encryption-decryption-->
    - [Encryption and Decryption Overview and Algorithm Specifications](huks-encryption-decryption-overview.md)
    - Development<!--huks-encryption-decryption-dev-->
      - [Encryption and Decryption (ArkTS)](huks-encryption-decryption-arkts.md)
      - [Encryption and Decryption (C/C++)](huks-encryption-decryption-ndk.md)
  - Signing and Signature Verification<!--huks-signing-signature-verification-->
    - [Signing and Signature Verification Overview and Algorithm Specifications](huks-signing-signature-verification-overview.md)
    - Development<!--huks-signing-signature-verification-dev-->
      - [Signing and Signature Verification (ArkTS)](huks-signing-signature-verification-arkts.md)
      - [Signing and Signature Verification (C/C++)](huks-signing-signature-verification-ndk.md)
  - Key Agreement<!--huks-key-agreement-->
    - [Key Agreement Overview and Algorithm Specifications](huks-key-agreement-overview.md)
    - Development<!--huks-key-agreement-dev-->
      - [Key Agreement (ArkTS)](huks-key-agreement-arkts.md)
      - [Key Agreement (C/C++)](huks-key-agreement-ndk.md)
  - Key Derivation<!--huks-key-derivation-->
    - [Key Derivation Overview and Algorithm Specifications](huks-key-derivation-overview.md)
    - Development<!--huks-key-derivation-dev-->
      - [Key Derivation (ArkTS)](huks-key-derivation-arkts.md)
      - [Key Derivation (C/C++)](huks-key-derivation-ndk.md)
  - Access Control <!--huks-identity-authentication-->
    - [HUKS Access Control Overview](huks-identity-authentication-overview.md)
    - Development<!--huks-identity-authentication-dev-->
      - [HUKS Access Control Development](huks-user-identity-authentication.md)
      - [Refined Access Control Development](huks-refined-user-identity-authentication.md)
  - HMAC<!--huks-hmac-->
    - [HMAC Overview and Algorithm Specifications](huks-hmac-overview.md)
    - Development<!--huks-hmac-dev-->
      - [HMAC(ArkTS)](huks-hmac-arkts.md)
      - [HMAC(C/C++)](huks-hmac-ndk.md)
- Key Deletion <!--huks-delete-key-->
  - [Deleting a Key (ArkTS)](huks-delete-key-arkts.md)
  - [Deleting a Key (C/C++)](huks-delete-key-ndk.md)
- Key Attestation<!--huks-key-attestation-->
  - [Key Attestation Overview and Algorithm Specifications](huks-key-attestation-overview.md)
  - Development<!--huks-key-attestation-dev-->
    - [Anonymous Key Attestation (ArkTS)](huks-key-anon-attestation-arkts.md)
    - [Anonymous Key Attestation (C/C++)](huks-key-anon-attestation-ndk.md)
    <!--Del-->
    - [Non-anonymous Key Attestation (for System Applications Only) (ArkTS)](huks-key-attestation-arkts-sys.md)
    - [Non-anonymous Key Attestation (for System Applications Only) (C/C++)](huks-key-attestation-ndk-sys.md)
    <!--DelEnd-->
- Other Operations<!--huks-other-operations-->
  - Checking Key Existence<!--huks-check-key-->
    - [Checking a Key (ArkTS)](huks-check-key-arkts.md)
    - [Checking a Key (C/C++)](huks-check-key-ndk.md)
  - Obtaining Key Properties<!--huks-obtain-key-properties-->
    - [Obtaining Key Properties (ArkTS)](huks-obtain-key-properties-arkts.md)
    - [Obtaining Key Properties (C/C++)](huks-obtain-key-properties-ndk.md)
  - Exporting a Key<!--huks-export-key-->
    - [Exporting a Key (ArkTS)](huks-export-key-arkts.md)
    - [Exporting a Key (C/C++)](huks-export-key-ndk.md)
  - Querying Key Aliases<!--huks-list-aliases-->
    - [Querying Key Aliases (ArkTS)](huks-list-aliases-arkts.md)
    - [Querying Key Aliases (C/C++)](huks-list-aliases-ndk.md)
  <!--Del-->
  - [Specifying the User for Key Operations (for System Applications Only)](huks-as-user-sys.md)
  <!--DelEnd-->
