# Universal Keystore Kit（密钥管理服务）

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

- Universal Keystore Kit简介
- 本地密钥管理<!--huks-local-key-management-->
  - 本地密钥管理基础概念
  - 密钥生成/导入<!--huks-key-generation-import-->
    - 密钥生成<!--huks-key-generation-->
      - 密钥生成介绍及算法规格
      - 生成密钥(ArkTS)
      - 生成密钥(C/C++)
    - 密钥导入<!--huks-key-import-->
      - 密钥导入介绍及算法规格
      - 明文导入密钥(ArkTS)
      - 明文导入密钥(C/C++)
      - 安全导入密钥(ArkTS)
      - 安全导入密钥(C/C++)
      - 数字信封导入密钥(ArkTS)
      - 数字信封导入密钥(C/C++)
  - 密钥使用<!--huks-key-use-->
    - 密钥使用介绍及通用流程
    - 加密/解密<!--huks-encryption-decryption-->
      - 加密/解密介绍及算法规格
      - 加解密(ArkTS)
      - 加解密(C/C++)
    - 签名/验签<!--huks-signing-signature-verification-->
      - 签名/验签介绍及算法规格
      - 签名/验签(ArkTS)
      - 签名/验签(C/C++)
    - 密钥协商<!--huks-key-agreement-->
      - 密钥协商介绍及算法规格
      - 密钥协商(ArkTS)
      - 密钥协商(C/C++)
    - 密钥封装<!--huks-kem-->
      - 密钥封装机制介绍及算法规格
      - 密钥封装(ArkTS)
    - 密钥派生<!--huks-key-derivation-->
      - 密钥派生介绍及算法规格
      - 密钥派生(ArkTS)
      - 密钥派生(C/C++)
    - 访问控制<!--huks-identity-authentication-->
      - 用户身份认证访问控制简介
      - 用户身份认证访问控制开发指导
      - 细粒度用户身份认证访问控制开发指导
    - HMAC<!--huks-hmac-->
      - HMAC介绍及算法规格
      - HMAC(ArkTS)
      - HMAC(C/C++)<!--RP1--><!--RP1End-->
  - 密钥删除<!--huks-delete-key-->
    - 密钥删除(ArkTS)
    - 密钥删除(C/C++)
  - 密钥证明<!--huks-key-attestation-->
    - 密钥证明介绍及算法规格
    - 匿名密钥证明(ArkTS)
    - 匿名密钥证明(C/C++)
    - 离线匿名密钥证明(ArkTS)<!--RP3--><!--RP3End-->
    <!--Del-->
    - 非匿名密钥证明(仅对系统应用开放)(ArkTS)
    - 非匿名密钥证明(仅对系统应用开放)(C/C++)
    <!--DelEnd-->
  - 其他操作<!--huks-other-operations-->
    - 查询密钥是否存在<!--huks-check-key-->
      - 查询密钥是否存在(ArkTS)
      - 查询密钥是否存在(C/C++)
    - 获取密钥属性<!--huks-obtain-key-properties-->
      - 获取密钥属性(ArkTS)
      - 获取密钥属性(C/C++)
    - 密钥导出<!--huks-export-key-->
      - 密钥导出(ArkTS)
      - 密钥导出(C/C++)
    - 查询密钥别名集<!--huks-list-aliases-->
      - 查询密钥别名集(ArkTS)
      - 查询密钥别名集(C/C++)<!--RP2--><!--RP2End-->
    - 群组密钥<!--huks-group-key-->
      - 群组密钥介绍
      - 群组密钥(ArkTS)
      - 群组密钥(C/C++)
    <!--Del-->
    - 指定用户身份操作（仅对系统应用开放）
    <!--DelEnd-->
- 密钥管理扩展<!--huks-key-management-extension-->
  - 密钥管理扩展介绍
  - CryptoExtensionAbility适配<!--huks-cryptoextensionability-adaptation-->
    - CryptoExtensionAbility扩展能力介绍
    - CryptoExtensionAbility适配开发指导
    - CryptoExtensionAbility注册与注销
  - 密钥管理扩展使用<!--huks-key-management-extension-usage-->
    - 密钥生成与导入导出
    - 签名/验签
    - PIN码访问控制
    - 通用操作
- 应用场景<!--huks-application-scenarios-->
  - 浏览器双向SSL登录
<!--RP4--><!--RP4End-->
- Universal Keystore Kit术语
