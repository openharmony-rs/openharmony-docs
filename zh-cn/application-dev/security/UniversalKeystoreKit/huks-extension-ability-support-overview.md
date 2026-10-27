# CryptoExtensionAbility扩展能力介绍

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

CryptoExtensionAbility是Stage模型中扩展组件[ExtensionAbility](../../application-models/extensionability-overview.md)的派生类。

CryptoExtensionAbility给驱动厂商提供外部密钥管理扩展能力所需接口定义，包括打开/关闭资源、PIN码认证、签名验签、导出证书等接口。

CryptoExtensionAbility可以隔离底层硬件（UKey驱动）厂商实现差异。

三方驱动HAP应用如需定义自身外部密钥管理扩展能力：

密钥管理扩展应用从开发、注册到注销的完整生命周期分为三个阶段：

1. 接口实现：继承CryptoExtensionAbility，根据业务需要实现[核心能力实现](#核心能力实现)中的回调接口，封装对底层外部密钥管理后端的调用。

2. 注册到HUKS：在密钥管理扩展设备/服务可用时调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)将CryptoExtensionAbility注册到HUKS。注册成功后，HUKS和证书管理将对应的密钥管理扩展能力开放给应用。

3. 注销下线：在设备拔出、服务停止等不可用场景下调用[unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider)注销已注册的能力，避免资源残留。

## 接入能力

密钥管理扩展应用需实现以下机制，使单个ExtensionAbility实例能够安全地管理一个或多个外部密钥管理资源（如UKey物理设备、软件资源等）。

在介绍具体机制前，需先明确两个核心概念：

- Provider：代表一个外部密钥管理驱动的逻辑归属，用于在HUKS中唯一标识该驱动。一般情况下，一个密钥管理扩展应用注册一个Provider，命名建议包含外部密钥管理能力提供方信息以保证全局唯一。

- Ability：代表开发者针对各业务定制的扩展能力，标识一个CryptoExtensionAbility实例的逻辑名。一个Provider下可注册多个Ability，对应密钥管理扩展应用中不同的CryptoExtensionAbility子类实例，用于在同一驱动下区分不同业务场景。

下文将依次介绍可用性检测、Provider/Ability约束、设备级资源隔离与定制化认证UI关联。

### 可用性检测与注册/注销时机

密钥管理扩展应用需根据接入的设备/服务形态，检测其可用性。当设备或服务可用时调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)接口注册CryptoExtensionAbility，不可用时调用[unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider)接口注销CryptoExtensionAbility，可参考[CryptoExtensionAbility注册与注销](huks-extension-registration-and-unregistration-arkts.md)。

检测机制因设备形态而异：
- UKey物理设备：监听USB插拔事件。
- 其他形态：根据服务可用性自行实现。

### Provider与Ability管理

一个Provider可以关联多个CryptoExtensionAbility。建议使用时按一对一方式进行匹配。

- Provider名称长度最大为128字节，建议包含外部密钥管理能力提供方信息以保证全局唯一。
- 整个系统最多支持注册**10个**CryptoExtensionAbility Provider，超过限制时registerProvider接口返回HUKS_ERR_CODE_EXCEED_LIMIT。
- 注册时由`(providerName, abilityName, bundleName)`三元组唯一标识。

### 设备级资源隔离

建议密钥管理扩展应用保障不同外部密钥管理资源的设备句柄、资源映射、会话状态、认证状态等相互独立。

### 定制化认证UI

系统提供PIN码认证弹窗能力，供上层应用在需要时拉起UKey PIN认证界面。若系统默认弹窗不满足业务需求，密钥管理扩展应用可注册自定义认证UI，在注册Provider时同步关联，由证书管理在需要时统一拉起。

从API版本26.0.0开始，支持注册[UIAbility](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability)作为自定义认证UI，开发者自行实现UI布局与交互逻辑。该方式仅支持由上层应用拉起，依赖调用方持有上下文信息。

从API版本26.0.1开始，新增支持注册[UkeyAuthExtensionAbility](../../reference/apis-device-certificate-kit/js-apis-UkeyAuthExtensionAbility.md#ukeyauthextensionability)作为自定义认证UI，开发者继承后自行实现UI布局与交互逻辑。该方式支持两种拉起路径：一种由上层应用拉起，依赖调用方持有上下文信息；另一种由UKey驱动应用主动拉起，不依赖上层应用持有上下文信息。

- 数量限制：同一resourceId字段对应的资源，仅支持关联一种类型的定制化认证UI（UIAbility或UkeyAuthExtensionAbility），不可同时注册两种类型。1个CryptoExtensionAbility最多关联**10个**自定义认证UI，超出时registerProvider返回HUKS_ERR_CODE_EXCEED_LIMIT。
- 字段说明：在注册密钥管理扩展时同步注册对应的定制化认证UI弹窗，通过[HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入JSON字符串，其中abilityName字段对应module.json5中name字段，最大长度为127字节，index字段对应resourceId，最大长度为512字节，用于将定制化认证UI路由到具体资源。
- 典型场景：自定义PIN输入框、自定义证书选择界面、自定义用户确认对话框等。

两种方式的差异如下：

| 维度 | UIAbility（26.0.0+） | UkeyAuthExtensionAbility（26.0.1+） |
| --- | --- | --- |
| 实现方式 | 开发者自实现UIAbility。 | 开发者继承UkeyAuthExtensionAbility自实现。 |
| abilityType | 0（或不传，默认按UIAbility处理） | 1 |
| 拉起方 | 上层应用。 | 上层应用或UKey驱动应用。 |
| 拉起接口 | [openUkeyAuthDialog()](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenukeyauthdialog22) | [openUkeyAuthDialog()](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenukeyauthdialog22)或[openAuthDialogForUkeyProvider()](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthdialogforukeyprovider) |
| 上下文依赖 | 依赖调用方持有上下文信息。 | 依赖上下文（上层应用拉起）或不依赖上下文（UKey驱动应用拉起）。 |
| 弹窗行为 | 普通应用窗口，支持前后台切换，可被切到后台。 | 模态系统弹窗，在用户完成交互前整个系统进入模态状态，无法切到后台或关闭。 |

## 核心能力实现

CryptoExtensionAbility主要实现以下能力：

1. 设备管理，支持单个ExtensionAbility连接多个UKey。
   - 单个ExtensionAbility最多支持连接10个UKey设备。
   - 需实现设备热插拔检测和管理机制，确保在UKey插入/拔出时，能及时通知ExtensionAbility。
   - 需实现设备级别的资源隔离，确保每个UKey设备的资源对其他UKey设备是不可见的。
2. 句柄管理，针对同一个UKey资源（例如容器下的密钥），支持应用维度句柄资源管理，通过[onOpenResource](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onopenresource)打开资源，通过[onCloseResource](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#oncloseresource)关闭资源。
   - 单个ExtensionAbility最多支持打开100个UKey密钥资源句柄。
   - 打开资源时需打开底层UKey句柄，并映射为新的句柄返回给HUKS。
   - 关闭资源时需关闭底层UKey句柄，并释放缓存的句柄映射。
   - 支持多个OpenHarmony应用，打开/关闭同一个UKey密钥资源。例如：OpenHarmony应用1，打开容器A后， OpenHarmony应用2，也可以再次打开容器A。
   - 支持多个OpenHarmony应用，操作同一个UKey密钥资源。例如：OpenHarmony应用1操作容器A中的私钥签名后，OpenHarmony应用2也验证PIN码后，也可以操作容器A中的私钥进行签名，两者互不影响。
3. 密钥会话管理，支持三段式密钥管理操作，单次签名验签需通过[onInitSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#oninitsession)/[onUpdateSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onupdatesession)/[onFinishSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onfinishsession)三个函数三步配合完成，需支持会话管理，缓存密钥会话状态。
   - init操作，初始化密钥会话，并返回会话句柄信息。
   - update操作，传入分组数据，对分组数据进行密码操作，更新密钥会话信息后，将中间数据（如果有）返回。
   - finish操作，对传入最后一段分组数据，进行密钥返回操作，并结束密钥会话，将最终结果返回。
4. 认证状态管理，支持应用维度的认证状态管理（认证/查询/重置）。针对同一个UKey中的应用A，OpenHarmony应用1验证UKey应用A的PIN码后，OpenHarmony应用2如果要访问UKey应用A，也需要进行PIN码认证操作。
5. 证书查询，支持根据证书类型，枚举所有证书或查询单个容器中的证书。
6. 通用查询，支持通用查询操作，为上层业务应用提供UKey设备信息、PIN码信息、公钥信息等查询能力。接口的属性ID采用定义在GMT 0016-2023 标准中的SKF函数名称，长度必须介于 1-100 字节。调用端和ExtensionAbility实现需约定使用的函数名集合及其参数/返回格式。