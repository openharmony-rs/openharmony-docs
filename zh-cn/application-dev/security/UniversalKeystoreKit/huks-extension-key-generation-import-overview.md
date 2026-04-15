# 外部密钥管理扩展密钥生成与导入介绍

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS提供密钥生成与导入能力，支持在外部密钥管理扩展场景下，在扩展设备内生成密钥对或导入加密封装的密钥对。

## 功能概述

在外部密钥管理扩展场景下，密钥生成与导入能力由[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)提供，驱动厂商需继承CryptoExtensionAbility并实现相关接口。

### 密钥生成

密钥生成指在扩展设备内生成非对称密钥对（如RSA、ECC密钥对）。生成的密钥存储在扩展设备中，私钥不会离开扩展设备，公钥可通过导出接口获取。

应用通过调用HUKS的[generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#generatekeyitem)接口发起密钥生成请求，HUKS根据资源ID索引到对应的Extension proxy，将请求转发给CryptoExtensionAbility的[onGenerateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityongeneratekeyitem26)接口完成密钥生成。

### 密钥导入

密钥导入指将加密封装的密钥对导入到扩展设备中。加密封装的密钥对通常由安全协商密钥加密，确保密钥在传输过程中不被泄露。

应用通过调用HUKS的[importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#importwrappedkeyitem)接口发起密钥导入请求，HUKS根据资源ID索引到对应的Extension proxy，将请求转发给CryptoExtensionAbility的[onImportWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonimportwrappedkeyitem26)接口完成密钥导入。

### 公钥导出

公钥导出指从扩展设备中导出指定密钥的公钥。导出的公钥可用于证书申请、密钥协商等场景。

应用通过调用HUKS的[exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#exportkeyitem)接口发起公钥导出请求，HUKS根据资源ID索引到对应的Extension proxy，将请求转发给CryptoExtensionAbility的[onExportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonexportkeyitem26)接口完成公钥导出。

## 规格差异说明

> **说明：**
>
> 以上接口复用HUKS原有接口定义。在外部密钥管理扩展场景下，密钥用途等参数传递给Extension后，由Extension实现方根据业务场景自行处理，HUKS不做额外校验。

## 接口列表

以下为密钥生成与导入相关的接口列表：

| 接口名 | 功能描述 | API级别 |
| -------- | -------- | -------- |
| [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#generatekeyitem) | 在扩展设备内生成密钥对 | 26+ |
| [importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#importwrappedkeyitem) | 导入加密封装的密钥对 | 26+ |
| [exportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#exportkeyitem) | 导出指定密钥的公钥 | 26+ |
| [onGenerateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityongeneratekeyitem26) | Extension实现的密钥生成接口 | 26+ |
| [onImportWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonimportwrappedkeyitem26) | Extension实现的密钥导入接口 | 26+ |
| [onExportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonexportkeyitem26) | Extension实现的公钥导出接口 | 26+ |

## 开发流程

密钥生成与导入的开发流程如下：

1. **获取资源ID**：通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。

2. **打开资源**：通过[openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource26)打开指定资源，获取资源句柄。

3. **密钥操作**：
   - 密钥生成：调用[generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#generatekeyitem)生成密钥对。
   - 密钥导入：调用[importWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#importwrappedkeyitem)导入加密封装的密钥对。

4. **关闭资源**：通过[closeResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptocloseresource26)关闭资源句柄。

公钥导出为独立功能，具体请参考[公钥导出(ArkTS)](huks-extension-key-export-arkts.md)。

具体开发示例请参考：
- [密钥生成(ArkTS)](huks-extension-key-generation-arkts.md)
- [密钥导入(ArkTS)](huks-extension-key-import-arkts.md)

## 相关文档

- [外部密钥管理扩展简介](huks-external-hardware-key-management-overview.md)
- [CryptoExtensionAbility扩展能力介绍](huks-extension-ability-support-overview.md)
- [CryptoExtensionAbility适配开发指导](huks-extension-ability-support-dev.md)
- [获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)