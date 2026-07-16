# 跨设备组件启动规则（Stage模型）

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本文介绍第三方应用跨设备启动[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)和[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)的约束规则。

## 协同接口列表

| 分类 | 接口 | 适用场景 |
| --- | --- | --- |
| 多轮交互 | [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | 支持跨设备启动UIAbility组件，并支持多轮交互。<br>注：该接口依赖WLAN开启。推荐优先使用，其连接速度更快、传输性能更优，详情请参考[跨设备连接UIAbility开发指南](../distributedservice/abilityconnectmanager-guidelines.md)。 |
| 多轮交互 | [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | 支持跨设备启动ExtensionAbility组件，并支持多轮交互。 |
| 多轮交互 | [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | 支持跨设备启动同一应用（相同APPID）的UIAbility组件，并支持多轮交互。 |
| 单次启动 | [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | 支持UIAbility组件间的跨设备单次启动。 |
| 单次启动 | [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startAbilityForResult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | 支持UIAbility组件间的跨设备单次启动，并可在目标组件调用terminateSelfWithResult销毁时获取返回结果。 |

## 跨设备组件启动条件

跨设备启动组件需同时满足以下三类条件：

1. **设备间可信关系**：双端设备需登录同一华为账号；若非同账号环境，需先通过[设备发现](../distributedservice/devicemanager-guidelines.md#设备发现开发指导)和[设备绑定](../distributedservice/devicemanager-guidelines.md#设备绑定开发指导)建立设备间可信关系。

2. **分布式设备安全等级要求**：取决于目标组件在module.json5文件中abilities标签的`exported`配置：
   - 值为`false`（缺省值）时，发起方设备的安全等级须 ≥ 目标方设备。
   - 值为`true`时，无安全等级要求。

3. **应用权限要求**：具体权限要求详见下表。

| 分类 | 接口 | 发起方权限要求（目标组件权限） | 发起方与被启动方权限要求（分布式协同权限） |
| --- | --- | --- | --- |
| 多轮交互 | [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | 若目标组件在module.json5文件中配置了abilities标签的`permissions`，调用方须持有其中全部权限 | ① ohos.permission.DISTRIBUTED_DATASYNC<br>② ohos.permission.GET_NETWORK_INFO<br>③ ohos.permission.SET_NETWORK_INFO<br>④ ohos.permission.INTERNET |
| 多轮交互 | [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | 若目标组件在module.json5文件中配置了abilities标签的`permissions`，调用方须持有其中全部权限 | ohos.permission.DISTRIBUTED_DATASYNC<br>注：该权限仅在应用间建链操作时由软总线校验，应用拉起阶段不校验。 |
| 多轮交互 | [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | 无要求（因仅限同应用内调用） | ohos.permission.DISTRIBUTED_DATASYNC<br>注：该权限仅在应用间建链操作时由软总线校验，应用拉起阶段不校验。 |
| 单次启动 | [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | 若目标组件在module.json5文件中配置了abilities标签的`permissions`，调用方须持有其中全部权限 | 无要求（因单次启动无多轮交互） |
| 单次启动 | [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startAbilityForResult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | 若目标组件在module.json5文件中配置了abilities标签的`permissions`，调用方须持有其中全部权限 | 无要求（因单次启动无多轮交互） |

> **说明：**
> - 权限申请方式详见[声明权限](../security/AccessToken/declare-permissions.md)。

## 跨设备启动流程

跨设备启动组件的校验流程如下图所示：

<div align="center">

![component-startup-rules-cross-device](figures/component-startup-rules-cross-device.png)

</div>
