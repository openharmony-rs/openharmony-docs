# 跨设备组件启动规则（Stage模型）

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

在跨设备协同场景中，应用常需启动其他设备上的 [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) 或 [ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md) 组件以实现多端交互。跨设备启动涉及设备可信关系、安全等级匹配及权限校验等多重约束，未满足规则将导致启动失败。本文档梳理了跨设备启动组件的完整规则，涵盖协同接口选型、启动条件及校验流程，适用于开发者在实现跨设备组件启动与多端协同功能时参考，以规范接口调用并快速定位启动异常。

## 基本概念

- **多轮交互**：启动方与目标方组件建立连接后，可进行多次数据通信与业务交互。
- **单次交互**：启动方启动目标方组件后，仅获取启动结果或目标方销毁时返回的结果，无后续多轮通信。
- **设备安全等级**：根据设备安全能力（例如：TEE、安全存储芯片等）划分的等级，等级越高安全能力越强。详情参考 [设备安全等级](../database/native-access-control-by-device-and-data-level.md#设备安全等级)。

## 协同接口

| 分类 | 接口 | 适用场景 |
| --- | --- | --- |
| 多轮交互 | [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | 支持跨设备启动 UIAbility 组件；推荐优先使用该接口，协同连接速度更快且传输性能更优，具体请参考 [跨设备连接 UIAbility 开发指南](../distributedservice/abilityconnectmanager-guidelines.md)。 |
| 多轮交互 | [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | 支持跨设备启动 ExtensionAbility 组件。 |
| 多轮交互 | [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | 支持跨设备启动同一应用（相同 APPID）间的 UIAbility 组件。 |
| 单次交互 | [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | 支持跨设备启动 UIAbility 组件的单次交互，仅返回启动结果。 |
| 单次交互 | [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | 支持跨设备启动 UIAbility 组件的单次交互，且支持由目标方组件调用 terminateSelfWithResult 销毁时返回详细结果。 |

## 启动条件

跨设备启动组件需同时满足以下三项要求：

1. 设备间可信关系要求
   - 双端设备登录同一账号，满足可信关系要求。
   - 双端设备非同账号，需通过 [设备发现](../distributedservice/devicemanager-guidelines.md#设备发现开发指导) 和 [设备绑定](../distributedservice/devicemanager-guidelines.md#设备绑定开发指导) 提前建立可信关系。

2. 分布式设备安全等级要求

   取决于目标方组件在 [module.json5](../quick-start/module-configuration-file.md) 文件中 abilities 标签的 `exported` 配置值：

   - `false`（缺省值），要求启动方所属设备安全等级 ≥ 目标方设备安全等级，且启动方和目标方是同一应用（相同 APPID）。
   - `true`，无安全等级要求。

3. 应用权限要求

| 接口 | 目标方对启动方的权限要求 | 启动方与目标方的分布式协同相关权限要求 |
| --- | --- | --- |
| [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | 若目标方在 module.json5 文件中配置了 abilities 标签的 `permissions`，启动方须持有其中全部权限。 | ohos.permission.DISTRIBUTED_DATASYNC<br>ohos.permission.GET_NETWORK_INFO<br>ohos.permission.SET_NETWORK_INFO<br>ohos.permission.INTERNET |
| [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | 若目标方在 module.json5 文件中配置了 abilities 标签的 `permissions`，启动方须持有其中全部权限。 | ohos.permission.DISTRIBUTED_DATASYNC |
| [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | 无要求（仅限同一应用间调用）。 | ohos.permission.DISTRIBUTED_DATASYNC |
| [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | 若目标方在 module.json5 文件中配置了 abilities 标签的 `permissions`，启动方须持有其中全部权限。 | 无要求（仅单次交互）。 |
| [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | 若目标方在 module.json5 文件中配置了 abilities 标签的 `permissions`，启动方须持有其中全部权限。 | 无要求（仅单次交互）。 |

> **说明：**
> - 权限的申请方式请参考 [声明权限](../security/AccessToken/declare-permissions.md)。
> - connectServiceExtensionAbility 和 startAbilityByCall 所需的 ohos.permission.DISTRIBUTED_DATASYNC 权限，在应用拉起阶段不校验，仅在应用间建链操作时由软总线校验。
