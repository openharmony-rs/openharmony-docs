# 外部密钥管理扩展简介

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS提供外部密钥管理扩展能力，允许三方驱动HAP应用注册、注销自定义的硬件密钥管理模块。用于满足金融领域基于Ukey的浏览器双向SSL认证等场景的身份认证诉求。

总体流程如下：
1. 驱动HAP应用根据业务场景编写应用自身的密钥管理拓展能力。
2. 驱动HAP需要将密钥管理扩展能力注册到系统HUKS服务中。
3. 浏览器等应用通过HUKS和[证书管理](../DeviceCertificateKit/certManager-overview.md)提供的API去使用驱动HAP提供的外部应用管理能力。包括证书查询、PIN码认证、签名验签等操作。

整体架构如下：
1. 外部密钥管理扩展能力，需要驱动HAP应用开发。
2. 通过HUKS和[证书管理](../DeviceCertificateKit/certManager-overview.md)的SDK将驱动HAP提供的外部密钥管理能力开放出去。

流程如下图所示：

<div align=center>

<img src=figures/huks_extension.png width=80% align=center/>

</div>

核心功能：
HUKS提供Provider管理接口，用于驱动HAP应用注册、注销外部密钥管理扩展能力。提供资源管理、PIN码管理、三段式密钥操作等能力，用于浏览器等应用操作外部密钥管理拓展中的密钥。

## Provider管理

| 功能 | 说明 |
| -------- | -------- |
| **[Provider管理](huks-provider-management-overview.md)** | 注册与注销外部硬件密钥的提供者。 |

## 资源管理

| 功能 | 说明 |
| -------- | -------- |
| **[资源管理](huks-resource-management-overview.md)** | 打开与关闭句柄资源。 |

## 外部密钥操作

| 功能 | 说明 |
| -------- | -------- |
| **[Ukey PIN码认证](huks-ukey-pin-authentication-management-overview.md)** | PC浏览器通过Ukey完成双向SSL认证，可获取认证状态。 |
| **[签名验签](huks-ukey-signing-signature-verification-overview.md)** | 用于认证消息内容以及消息发送者身份的真实性。 |

## 通用操作

| 功能 | 说明 |
| -------- | -------- |
| **[通用查询](huks-ukey-general-query-overview.md)** | 获取Ukey的密钥相关属性。 |

## ExtensionAbility扩展能力

| 功能 | 说明 |
| -------- | -------- |
| **[ExtensionAbility扩展能力](huks-extension-ability-support-overview.md)** | 应用接入ExtensionAbility。 |

## HUKS接入外部硬件密钥管理

HUKS接入外部硬件密钥管理，需要实现CryptoExtensionAbility接口。在开发前，需要先了解ExtensionAbility组件，建议参考[ExtensionAbility组件概述](../../application-models/extensionability-overview.md)。

CryptoExtensionAbility是Stage模型中扩展组件ExtensionAbility的派生类。开发者可以通过修改配置文件，定制外部硬件密钥管理的行为，包括：调用外部硬件密钥管理的接口、外部硬件密钥管理的实现、外部硬件密钥管理的配置等，可以参考[ExtensionAbility适配开发指导](huks-extension-ability-support-dev.md)。