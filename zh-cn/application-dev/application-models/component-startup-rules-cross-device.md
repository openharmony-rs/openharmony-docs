# 跨设备组件启动规则

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

在跨设备协同场景中，应用常需启动其他设备上的UIAbility或ExtensionAbility组件以实现多端交互。跨设备启动涉及设备可信关系、安全等级匹配及权限校验等多重约束，未满足规则将导致启动失败。本文档梳理了跨设备启动组件的完整规则，涵盖协同接口选型、启动条件及校验流程，适用于开发者在实现跨设备组件启动与多端协同功能时参考，以规范接口调用并快速定位启动异常。

## 基本概念

- **多轮交互**：启动方与目标方组件建立连接后，可进行多次数据通信与业务交互。
- **单次交互**：启动方启动目标方组件后，仅获取启动结果或目标方销毁时返回的结果，无后续多轮通信。
- **设备安全等级**：根据设备安全能力（例如：TEE、安全存储芯片等）划分的等级，等级越高安全能力越强。详情参考设备安全等级。

## 协同接口

| 分类 | 接口 | 适用场景 |
| --- | --- | --- |
| 多轮交互 | abilityConnectionManager | 支持跨设备启动UIAbility组件；推荐优先使用该接口，协同连接速度更快且传输性能更优，具体请参考跨设备连接UIAbility开发指南。 |
| 多轮交互 | connectServiceExtensionAbility | 支持跨设备启动ExtensionAbility组件。 |
| 多轮交互 | startAbilityByCall | 支持跨设备启动同一应用（相同APPID）间的UIAbility组件。 |
| 单次交互 | startAbility | 支持跨设备启动UIAbility组件的单次交互，仅返回启动结果。 |
| 单次交互 | startAbilityForResult<br>terminateSelfWithResult | 支持跨设备启动UIAbility组件的单次交互，且支持由目标方组件调用terminateSelfWithResult销毁时返回详细结果。 |

## 启动条件

跨设备启动组件需同时满足以下三项要求：

1. 设备间可信关系要求

   - 双端设备登录同一账号，满足可信关系要求。
   - 双端设备非同账号，需通过设备发现和设备绑定提前建立可信关系。

2. 分布式设备安全等级要求

   取决于目标方组件在module.json5文件中abilities标签的`exported`配置值：

   - `false`（缺省值），要求启动方所属设备安全等级 ≥ 目标方设备安全等级，且启动方和目标方是同一应用（相同APPID）。
   - `true`，无安全等级要求。

3. 应用权限要求

| 接口 | 目标方对启动方的权限要求 | 启动方与目标方的分布式协同相关权限要求 |
| --- | --- | --- |
| abilityConnectionManager | 若目标方在module.json5文件中配置了abilities标签的`permissions`，启动方须持有其中全部权限。 | ohos.permission.DISTRIBUTED_DATASYNC<br>ohos.permission.GET_NETWORK_INFO<br>ohos.permission.SET_NETWORK_INFO<br>ohos.permission.INTERNET |
| connectServiceExtensionAbility | 若目标方在module.json5文件中配置了abilities标签的`permissions`，启动方须持有其中全部权限。 | ohos.permission.DISTRIBUTED_DATASYNC |
| startAbilityByCall | 无要求（仅限同一应用间调用）。 | ohos.permission.DISTRIBUTED_DATASYNC |
| startAbility | 若目标方在module.json5文件中配置了abilities标签的`permissions`，启动方须持有其中全部权限。 | 无要求（仅单次交互）。 |
| startAbilityForResult<br>terminateSelfWithResult | 若目标方在module.json5文件中配置了abilities标签的`permissions`，启动方须持有其中全部权限。 | 无要求（仅单次交互）。 |

> **说明**
>
> - 权限的申请方式请参考声明权限。
> - connectServiceExtensionAbility和startAbilityByCall所需的ohos.permission.DISTRIBUTED_DATASYNC权限，在应用拉起阶段不校验，仅在应用间建链操作时由软总线校验。
