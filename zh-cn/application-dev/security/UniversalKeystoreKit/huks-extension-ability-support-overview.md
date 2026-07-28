# CryptoExtensionAbility扩展能力介绍

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

CryptoExtensionAbility是Stage模型中扩展组件[ExtensionAbility](../../application-models/extensionability-overview.md)的派生类，用于隔离底层驱动厂商实现差异，将厂商自有的外部密钥管理能力接入 HUKS 框架，向上层应用提供签名验签、密钥使用、证书查询、PIN认证等能力。

本文档面向**密钥管理扩展应用开发者**，说明厂商在实现CryptoExtensionAbility时需要关注的接口、状态管理和约束限制。详细API参数和各接口建议返回的错误码请参考[@ohos.security.CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)。

三方驱动HAP应用如需定义自身密钥管理扩展能力：

1. 继承CryptoExtensionAbility，根据需要实现本文档列出的接口。

2. 在密钥管理扩展设备/服务可用时调用registerProvider注册，不可用时调用 unregisterProvider注销。具体的触发时机由接入形态决定（如UKey物理设备监听USB插拔，虚拟智能卡等则在应用启动或服务就绪时触发）。

3. 注册成功后，HUKS和证书管理将对应的密钥管理扩展能力开放给应用。

## 注册/注销

密钥管理扩展应用需实现以下机制，使单个ExtensionAbility实例能够安全地管理一个或多个外部密钥管理设备（如UKey物理设备、虚拟智能卡等）。

- 密钥管理扩展服务可用性检测：密钥管理扩展应用需根据接入的设备/服务形态，检测其可用性。当设备或服务可用调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)接口注册CryptoExtensionAbility，不可用时调用[unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider)接口注销CryptoExtensionAbility，可参考[注册/注销(ArkTS)](huks-extension-registration-and-unregistration-arkts.md)和[注册/注销(C/C++)](huks-extension-registration-and-unregistration-ndk.md)。检测机制因设备形态而异：
  - UKey物理设备：监听USB插拔事件。
  - 虚拟智能卡（数字盾）：应用启动、服务就绪等事件。
  - 其他形态：根据设备可用性自行实现。

- Provider限制：一个Provider可以关联到多个Ability。一般来说，Provider是厂商驱动名称，Ability是厂商针对各业务定制扩展能力的名称。
  - Provider名称长度最大为128字节，建议包含厂商信息以保证全局唯一。
  - 注册时由`(providerName, abilityName, bundleName)`三元组唯一标识，超过限制时registerProvider接口返回HUKS_ERR_CODE_EXCEED_LIMIT。
  - 整个系统最多支持注册**10个**CryptoExtensionAbility Provider。

- 设备级资源隔离：密钥管理扩展应用需确保不同外部密钥管理资源的设备句柄、资源映射、会话状态、认证状态等相互独立。

- UIExtensionAbility关联（从API版本26.0.0开始支持）：OpenHarmony中有两类ExtensionAbility配合使用——CryptoExtensionAbility处理密码学操作，UIExtensionAbility处理需要定制化的UI交互的流程（如PIN输入框、证书选择界面）。密钥管理扩展应用可在注册Provider时同步关联UIExtensionAbility：
  - 数量限制：1个CryptoExtensionAbility最多关联**10个**UIExtensionAbility，超出时registerProvider返回HUKS_ERR_CODE_EXCEED_LIMIT。
  - 字段说明：通过[HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入JSON字符串，其中abilityName字段对应module.json5中UIExtensionAbility的name字段，最大长度为128字节，index字段对应resourceId，最大长度为512字节，用于将UIExtensionAbility路由到具体资源。
  - 典型场景：自定义PIN输入框、自定义证书选择界面、自定义用户确认对话框等。

## 核心能力实现

CryptoExtensionAbility中共有17个接口，密钥管理扩展应用可根据业务按需实现其中部分接口。

17个接口按职责可分为7个能力域，部分能力域在实现时存在明确的依赖关系。

- [资源标识](#1-资源标识)和[句柄管理](#2-句柄管理)共同构成资源访问入口：上层应用先通过getResourceId接口获得resourceId，再通过openResource获得handle；密钥管理扩展应用需按`(UID, handle)`二元组维护应用级句柄与底层设备句柄的映射。
- [认证状态管理](#4-认证状态管理)是私钥操作的前置条件，以`(UID, 外部密钥管理资源Application)`为粒度维护PIN认证状态——使用私钥的所有操作（[密钥会话管理](#3-密钥会话管理)中的签名、[密钥生成/导入/导出](#)中的解密等）必须先完成PIN 认证。
- 公共操作（[属性查询与设置](#7-属性查询与设置)、[证书查询与导入](#6-证书查询与导入)、密钥管理中的生成/导出公钥）无需PIN认证。
- 密钥会话通过三段式协议（initSession/updateSession/finishSession）处理签名/验签的中间状态。

典型调用顺序为：资源标识 → 设备/服务可用时注册 → 打开资源 → 公共操作 → 私钥操作前PIN认证 → 签名/验签 → 关闭资源 → 设备/服务不可用时注销。

> **通用说明**：
> 1. CryptoExtensionAbility所有接口的params中都会携带调用方身份信息（通过HUKS_EXT_CRYPTO_TAG_UID标识）。密钥管理扩展应用可基于业务需要决定是否使用，例如在句柄管理、会话管理、认证管理等场景下基于UID进行隔离与权限校验。
> 2. 接口函数的resultCode不支持自定义，必须按[HuksCryptoExtensionResultCode](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensionresultcode)枚举定义的错误码返回，否则可能导致异常。
> 3. 从API版本26开始，厂商如需传递自定义的细粒度错误信息，可通过返回值的errInfo字段传入，errInfo为[HuksExternalErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalerrorinfo)类型。上层应用可通过[huksExternalCrypto.getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo)接口获取。

| 能力域 | 接口 | 起始版本 | 用途 |
|--------|------|---------|------|
| 资源标识 | onGetResourceId | 26 | 获取资源ID |
| 句柄管理 | onOpenResource | 22 | 打开UKey密钥资源 |
| 句柄管理 | onCloseResource | 22 | 关闭UKey密钥资源 |
| 认证状态管理 | onAuthUkeyPin | 22 | 验证PIN码 |
| 认证状态管理 | onGetUkeyPinAuthState | 22 | 查询PIN认证状态 |
| 认证状态管理 | onClearUkeyPinAuthState | 22 | 清除PIN认证状态 |
| 密钥生成/导入/导出 | onGenerateKeyItem | 26 | 在UKey内生成密钥对 |
| 密钥生成/导入/导出 | onExportKeyItem | 26 | 导出UKey内密钥的公钥 |
| 密钥生成/导入/导出 | onImportWrappedKeyItem | 26 | 导入加密封装的密钥对 |
| 密钥会话 | onInitSession | 22 | 三段式会话初始化 |
| 密钥会话 | onUpdateSession | 22 | 三段式会话更新（可调用0次或多次） |
| 密钥会话 | onFinishSession | 22 | 三段式会话结束 |
| 证书查询与导入 | onExportCertificate | 22 | 查询指定resourceId的证书 |
| 证书查询与导入 | onEnumCertificates | 22 | 枚举所有证书 |
| 证书查询与导入 | onImportCertificate | 26 | 导入证书到UKey |
| 属性查询与设置 | onGetProperty | 22 | 查询属性 |
| 属性查询与设置 | onSetProperty | 26 | 设置属性 |

> **说明**：标注26起始版本的接口需API版本26及以上才可使用，密钥管理扩展应用需根据目标API版本评估实现范围。

### 1. 资源标识

从API版本26.0.0开始，提供[onGetResourceId](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetresourceid)接口。根据厂商自定义的Provider/Ability/Bundle名称、调用方UID等参数，返回对应的resourceId。params中需携带以下必选参数：[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)表示Ability名称、[HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)表示Bundle名称、[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)表示厂商自定义的资源信息。

- 典型场景：上层应用通过业务标识调用getResourceId，密钥管理扩展服务返回对应的resourceId。业务标识的具体形态由接入的设备或服务定义，常见形态包括证书序列号、容器名、密钥别名等。

- 返回结构：成功时通过result.resourceId字段返回资源ID，可用于后续的openResource等接口，标识密钥管理扩展服务中的某个具体资源。

### 2. 句柄管理

针对同一个密钥管理扩展资源（例如容器下的密钥），需要通过句柄管理访问的生命周期。

- 打开资源：通过[onOpenResource](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onopenresource)接口打开resourceId标识的资源。
  - 密钥管理扩展应用需在内部建立resourceId与新句柄的映射（具体实现由接入的设备/服务决定，如UKey打开会话、数字盾启动服务等），并返回给HUKS，句柄值由厂商自行生成并保证唯一性。
  - 业务身份通过params参数中的HUKS_EXT_CRYPTO_TAG_UID携带，**密钥管理扩展应用需基于此UID做句柄资源的隔离存储**。

- 关闭资源：通过[onCloseResource](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#oncloseresource)接口关闭handle对应的资源，密钥管理扩展应用需在内部释放 resourceId与句柄的映射关系（具体实现由接入的设备/服务决定，如UKey关闭会话、数字盾停止服务等），并通知HUKS资源已关闭。

- 多应用并发：
  - 多个OpenHarmony应用可同时打开/关闭同一资源，**每个应用应获得独立的映射句柄**。例如：OpenHarmony应用1打开资源A后，OpenHarmony应用2也可以再次打开资源A。
  - 多个应用操作同一资源时（例如签名），**互不影响**，各自维护独立的句柄与会话。例如：OpenHarmony应用1使用私钥签名后，OpenHarmony应用2完成PIN认证后，也可以使用私钥签名，两者互不影响。

> 建议：句柄资源存储的key建议为`(UID, handle)`二元组，避免不同应用间的句柄冲突。

### 3. 认证状态管理

支持应用维度的PIN码认证状态管理（认证/查询/重置）。每个OpenHarmony应用需独立完成PIN认证。

- 认证状态维度：建议PIN认证以GM/T 0016-2023中定义的Application为单位，不同Application需独立认证。
  - OpenHarmony应用1完成Application A的PIN认证后，OpenHarmony应用2访问Application A仍需独立认证。
  - 同一应用访问不同Application，也需分别进行认证。

- PIN 加密传输：调用方传入的PIN是通过[onGetProperty](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetproperty) 中导出的公钥加密后的密文，密钥管理扩展应用在[onAuthUkeyPin](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onauthukeypin) 中需先使用对应私钥解密，再调用底层驱动进行验证。[onGetUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetukeypinauthstate)用于查询PIN认证状态。

- 重置范围：[onClearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onclearuKeypinauthstate) 用于清除**应用维度的认证状态**（不解除外部密钥管理设备本身的PIN锁定）。UKey物理PIN解锁需通过UKey物理按键或厂商私有通道完成，**不通过CryptoExtensionAbility接口暴露**。

### 4. 密钥生成/导入/导出

从API版本26.0.0开始，提供密钥的生成、公钥导出、加密封装密钥导入能力（密钥存储在外部密钥管理设备内）。

- 生成密钥：通过[onGenerateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongeneratekeyitem)接口在密钥管理扩展服务中生成密钥对。入参支持指定算法、密钥长度、用途，密钥管理扩展应用需设置合理默认值（如RSA-2048、签名用途）。返回成功表示密钥对已生成。

- 导出公钥：通过[onExportKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onexportkeyitem)接口从密钥管理扩展服务导出公钥。推荐传入密钥用途参数以导出指定用途的公钥，建议未指定时默认签名用途。导出的公钥数据通过result.outData返回。

- 导入封装密钥：通过[onImportWrappedKeyItem](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onimportwrappedkeyitem)接口将加密封装的密钥对导入到密钥管理扩展服务。需配合密钥管理扩展服务内的传输密钥（wrappingHandle）使用，wrappedKey数据格式由密钥管理扩展应用定义。典型场景：通过密钥管理扩展服务内的传输密钥安全导入外部生成的密钥对。

### 5. 密钥会话管理

签名/验签、加解密等操作采用三段式协议完成。

- 会话模型：
  - [onInitSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#oninitsession)：初始化密钥会话，返回新的会话handle。
  - [onUpdateSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onupdatesession)：传入分段数据（可调用0次或多次），执行中间密码运算。
  - [onFinishSession](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onfinishsession)：传入最后一段数据，执行最终密码运算，结束会话并返回最终结果。

- 状态缓存：厂商需缓存会话状态，至少应包含会话句柄与底层会话的映射、累积的中间数据、业务身份（通过HUKS_EXT_CRYPTO_TAG_UID传入）。

- 生命周期：底层资源不可用或ExtensionAbility销毁时，所有未结束的会话应被主动清理。

### 6. 证书查询与导入

密钥管理扩展应用可支持按证书用途[HUKS_EXT_CRYPTO_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)查询、枚举和导入证书。如未指定，密钥管理扩展应用需设置合理默认值（如签名用途的证书）。

- 证书用途过滤：通过`HUKS_EXT_CRYPTO_TAG_PURPOSE`参数指定，建议支持以下取值：
  - `0`：默认用途
  - `1`：查询所有凭据
  - `2`：凭据签名
  - `3`：凭据加密
  - 未指定时默认获取签名证书

- 证书查询：[onExportCertificate](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onexportcertificate)查询resourceId下的单个证书。

- 证书枚举：[onEnumCertificates](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onenumcertificates)枚举当前CryptoExtensionAbility下的所有证书。

- 返回结构：通过result.certs返回，元素类型为Array<[HuksCryptoExtensionCertInfo](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensioncertinfo)>。

- 证书导入（从API版本26.0.0起支持）：通过[onImportCertificate](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onimportcertificate)接口将证书导入密钥管理扩展服务。

### 7. 属性查询与设置

密钥管理扩展应用可支持对密钥管理扩展服务信息的查询与设置。

通过[onGetProperty](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#ongetproperty)接口可实现对设备信息、公钥等属性的查询；在API版本26.0.0之后，可通过[onSetProperty](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#onsetproperty)接口设置属性。

- propertyId命名约定：propertyId是上层应用与密钥管理扩展应用之间的调用契约，且长度必须介于1-100字节。上层应用调用时指定propertyId，密钥管理扩展应用在onGetProperty/onSetProperty中识别该propertyId并执行对应操作。两端需约定以下三项内容：
  - 函数名集合：驱动支持哪些propertyId、上层应用可调用哪些。
  - 参数格式：每个propertyId对应的入参结构。
  - 返回格式：每个propertyId对应的返回值结构。

- 必实现属性：在PIN认证流程中，HUKS框架会传入propertyId（SKF_ExportPublicKey），调用onGetProperty获取公钥，用于加密后续传入的PIN。密钥管理扩展应用必须实现SKF_ExportPublicKey属性。

> 建议：建议使用GM/T 0016-2023定义的SKF标准函数名作为propertyId，以保证不同厂商之间的互操作性。