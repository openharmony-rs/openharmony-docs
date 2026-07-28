# 密钥生成与导入导出介绍

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，HUKS提供密钥生成、导入与导出能力。在密钥管理扩展场景下（UKey物理设备、虚拟智能卡等），应用可通过HUKS标准接口在密钥管理扩展服务中生成密钥对、导入加密封装的密钥对或导出公钥。

调用方包括但不限于：三方应用、浏览器、内部模块（如证书管理）等。HUKS框架负责将接口调用转发到密钥管理扩展服务中完成实际操作。**调用方无需关心具体实现细节**。

## 功能概述

本节涵盖密钥生命周期的核心操作：

- 在密钥管理扩展场景下，keyAlias即为resourceId，即已执行过[打开资源](huks-open-close-resource-arkts.md#打开资源)操作，且keyAlias中包含的providerName、abilityName、bundleName内容一致。

- 调用时均需指定[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示该密钥由密钥管理扩展服务实现方管理，密钥用途等参数由密钥管理扩展服务实现方根据业务场景自行处理，**HUKS不做额外校验**。

### 密钥生成

在密钥管理扩展服务中生成非对称密钥对（如RSA、ECC密钥对）。生成的密钥存储在服务中，私钥不会离开服务提供方，公钥可通过导出接口获取。

应用通过调用HUKS的[generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9)接口发起密钥生成请求，请求被转发到CryptoExtensionAbility的[onGenerateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongeneratekeyitem)接口完成密钥生成。详细接口使用请参考[密钥生成(ArkTS)](huks-extension-key-generation-arkts.md)。

### 密钥安全导入

将加密封装的密钥对导入到密钥管理扩展服务中。封装密钥对通常由安全协商密钥加密，确保密钥在传输过程中不被泄露。

应用通过调用HUKS的[importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportwrappedkeyitem9)接口发起密钥安全导入请求，请求被转发到CryptoExtensionAbility的[onImportWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onimportwrappedkeyitem)接口完成密钥安全导入。详细接口使用请参考[密钥导入(ArkTS)](huks-extension-key-import-arkts.md)。

### 公钥导出

从密钥管理扩展服务中导出指定密钥的公钥。导出的公钥可用于证书申请、密钥协商、PIN加密等场景。

应用通过调用HUKS的[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksexportkeyitem9)接口发起公钥导出请求，请求被转发到CryptoExtensionAbility的[onExportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onexportkeyitem)接口完成公钥导出。详细接口使用请参考[密钥导出(ArkTS)](huks-extension-key-export-arkts.md)。

## 规格差异说明

以上接口复用HUKS原有接口定义。在密钥管理扩展场景下，params中的参数为可选参数，由密钥管理扩展服务实现方定义支持范围。如未传入相应参数，密钥管理扩展服务将使用设置的默认行为。

- **密钥生成（generateKeyItem）**：推荐传入算法类型（HUKS_TAG_ALGORITHM）、密钥长度（HUKS_TAG_KEY_SIZE）、密钥用途（HUKS_TAG_PURPOSE）等参数。如未传入，密钥管理扩展服务将使用默认值。keyAlias需传入有效的resourceId。
- **密钥安全导入（importWrappedKeyItem）**：推荐传入算法类型、密钥长度、密钥用途等参数。keyAlias和wrappingKeyAlias需传入有效的resourceId。wrappedKey为封装密钥数据，格式由密钥管理扩展服务实现方定义。
- **公钥导出（exportKeyItem）**：推荐传入密钥用途（HUKS_TAG_PURPOSE）参数，以便导出指定用途的公钥。如未传入，密钥管理扩展服务将使用默认值（通常默认签名用途）。keyAlias需传入有效的resourceId。