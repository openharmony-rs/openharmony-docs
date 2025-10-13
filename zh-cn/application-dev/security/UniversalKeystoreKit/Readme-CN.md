# Universal Keystore Kit（密钥管理服务）

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

- [Universal Keystore Kit简介](huks-overview.md)
- [通用密钥库基础概念](huks-concepts.md)
- 密钥生成/导入<!--huks-key-generation-import-->
  - 密钥生成<!--huks-key-generation-->
    - [密钥生成介绍及算法规格](huks-key-generation-overview.md)
    - 开发指导<!--huks-key-generation-dev-->
      - [生成密钥(ArkTS)](huks-key-generation-arkts.md)
      - [生成密钥(C/C++)](huks-key-generation-ndk.md)
  - 密钥导入<!--huks-key-import-->
    - [密钥导入介绍及算法规格](huks-key-import-overview.md)
    - 开发指导<!--huks-key-import-dev-->
      - [明文导入密钥(ArkTS)](huks-import-key-in-plaintext-arkts.md)
      - [明文导入密钥(C/C++)](huks-import-key-in-plaintext-ndk.md)
      - [加密导入密钥(ArkTS)](huks-import-wrapped-key-arkts.md)
      - [加密导入密钥(C/C++)](huks-import-wrapped-key-ndk.md)
- 密钥使用<!--huks-key-use-->
  - [密钥使用介绍及通用流程](huks-key-use-overview.md)
  - 加密/解密<!--huks-encryption-decryption-->
    - [加密/解密介绍及算法规格](huks-encryption-decryption-overview.md)
    - 开发指导<!--huks-encryption-decryption-dev-->
      - [加解密(ArkTS)](huks-encryption-decryption-arkts.md)
      - [加解密(C/C++)](huks-encryption-decryption-ndk.md)
  - 签名/验签<!--huks-signing-signature-verification-->
    - [签名/验签介绍及算法规格](huks-signing-signature-verification-overview.md)
    - 开发指导<!--huks-signing-signature-verification-dev-->
      - [签名/验签(ArkTS)](huks-signing-signature-verification-arkts.md)
      - [签名/验签(C/C++)](huks-signing-signature-verification-ndk.md)
  - 密钥协商<!--huks-key-agreement-->
    - [密钥协商介绍及算法规格](huks-key-agreement-overview.md)
    - 开发指导<!--huks-key-agreement-dev-->
      - [密钥协商(ArkTS)](huks-key-agreement-arkts.md)
      - [密钥协商(C/C++)](huks-key-agreement-ndk.md)
  - 密钥派生<!--huks-key-derivation-->
    - [密钥派生介绍及算法规格](huks-key-derivation-overview.md)
    - 开发指导<!--huks-key-derivation-dev-->
      - [密钥派生(ArkTS)](huks-key-derivation-arkts.md)
      - [密钥派生(C/C++)](huks-key-derivation-ndk.md)
  - 访问控制<!--huks-identity-authentication-->
    - [用户身份认证访问控制简介](huks-identity-authentication-overview.md)
    - 开发指导<!--huks-identity-authentication-dev-->
      - [用户身份认证访问控制开发指导](huks-user-identity-authentication.md)
      - [细粒度用户身份认证访问控制开发指导](huks-refined-user-identity-authentication.md)
  - HMAC<!--huks-hmac-->
    - [HMAC介绍及算法规格](huks-hmac-overview.md)
    - 开发指导<!--huks-hmac-dev-->
      - [HMAC(ArkTS)](huks-hmac-arkts.md)
      - [HMAC(C/C++)](huks-hmac-ndk.md)
- 密钥删除<!--huks-delete-key-->
  - [密钥删除(ArkTS)](huks-delete-key-arkts.md)
  - [密钥删除(C/C++)](huks-delete-key-ndk.md)
- 密钥证明<!--huks-key-attestation-->
  - [密钥证明介绍及算法规格](huks-key-attestation-overview.md)
  - 开发指导<!--huks-key-attestation-dev-->
    - [匿名密钥证明(ArkTS)](huks-key-anon-attestation-arkts.md)
    - [匿名密钥证明(C/C++)](huks-key-anon-attestation-ndk.md)
    <!--Del-->
    - [非匿名密钥证明(仅对系统应用开放)(ArkTS)](huks-key-attestation-arkts-sys.md)
    - [非匿名密钥证明(仅对系统应用开放)(C/C++)](huks-key-attestation-ndk-sys.md)
    <!--DelEnd-->
- 其他操作<!--huks-other-operations-->
  - 查询密钥是否存在<!--huks-check-key-->
    - [查询密钥是否存在(ArkTS)](huks-check-key-arkts.md)
    - [查询密钥是否存在(C/C++)](huks-check-key-ndk.md)
  - 获取密钥属性<!--huks-obtain-key-properties-->
    - [获取密钥属性(ArkTS)](huks-obtain-key-properties-arkts.md)
    - [获取密钥属性(C/C++)](huks-obtain-key-properties-ndk.md)
  - 密钥导出<!--huks-export-key-->
    - [密钥导出(ArkTS)](huks-export-key-arkts.md)
    - [密钥导出(C/C++)](huks-export-key-ndk.md)
  - 查询密钥别名集<!--huks-list-aliases-->
    - [查询密钥别名集(ArkTS)](huks-list-aliases-arkts.md)
    - [查询密钥别名集(C/C++)](huks-list-aliases-ndk.md)
  <!--Del-->
  - [指定用户身份操作(仅对系统应用开放)](huks-as-user-sys.md)
  <!--DelEnd-->