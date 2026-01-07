# CryptoExtensionAbility扩展能力介绍

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

CryptoExtensionAbility是Stage模型中扩展组件[ExtensionAbility](../../application-models/extensionability-overview.md)的派生类。

CryptoExtensionAbility给驱动厂商提供外部密钥管理扩展能力所需接口定义，包括打开/关闭资源、PIN码认证、签名验签、导出证书等接口。

CryptoExtensionAbility可以隔离底层硬件（Ukey驱动）厂商实现差异。

三方驱动HAP应用如需定义自身外部密钥管理扩展能力：

首先，需继承CryptoExtensionAbility并完成相关的接口实现。其次，通过Provider注册接口完成能力注册。最后，由HUKS和证书管理将对应的密钥管理扩展能力开放给应用。

## 核心能力实现

CryptoExtensionAbility主要实现以下能力：

1. 设备管理，单个ExtensionAbility实现，支持多个Ukey。
2. 句柄管理，针对同一个Ukey资源（例如容器下的密钥），支持应用维度句柄资源管理。
   - 支持多个OpenHarmony应用，打开同一个Ukey密钥资源。例如：OpenHarmony应用1，打开容器A后， OpenHarmony应用2，也可以再次打开容器A。
   - 支持多个OpenHarmony应用，操作同一个Ukey密钥资源。例如：OpenHarmony应用1操作容器A中的私钥签名后，OpenHarmony应用2也验证PIN码后，也可以操作容器A中的私钥进行签名，两者互不影响。
3. 密钥会话管理，支持三段式密钥管理操作，单次签名验签需通过[onInitSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityoninitsession)/[onUpdateSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonupdatesession)/[onFinishSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonfinishsession)三个函数三步配合完成，需支持会话管理，缓存密钥会话状态。
   - init操作，初始化密钥会话，并返回会话句柄信息。
   - update操作，传入分组数据，对分组数据进行密码操作，更新密钥会话信息后，将中间数据（如果有）返回。
   - finish操作，对传入最后一段分组数据，进行密钥返回操作，并结束密钥会话，将最终结果返回。
4. 认证状态管理，支持应用维度的认证状态管理。针对同一个Ukey中的应用A，OpenHarmony应用1验证Ukey应用A的PIN码后，OpenHarmony应用2如果要访问Ukey应用A，也需要进行PIN码认证操作。
5. 证书查询，支持根据证书类型，枚举所有证书或查询单个容器中的证书。