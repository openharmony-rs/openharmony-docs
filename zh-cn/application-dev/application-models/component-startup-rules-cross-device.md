# 跨设备组件启动规则（Stage模型）

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

为了保障系统安全与用户体验，系统限制了应用在后台状态时任意弹窗、相互唤醒以及前台应用任意跳转的行为。跨设备启动组件时，系统会在[设备内组件启动规则](./component-startup-rules-inner-device.md)的基础上，**再次进行跨设备维度的校验**。本文主要介绍第三方应用在跨设备启动[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)和[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)的约束规则。系统应用的跨设备启动规则请参考[跨设备组件启动规则（Stage模型）（仅对系统应用开放）](./component-startup-rules-cross-device-sys.md)。

> **说明：**
>
> - 组件启动规则自API version 9开始生效，新增规则生效版本在规则中单独说明。开发者需熟知组件启动规则，以避免业务功能异常。
> - 跨设备启动需同时满足设备内启动规则与跨设备启动规则，任一环节校验失败均会导致启动失败。
> - 第三方应用不支持申请后台启动权限（`ohos.permission.START_ABILITIES_FROM_BACKGROUND`）和拉起不可见组件权限（`ohos.permission.START_INVISIBLE_ABILITY`），因此**不支持后台拉起**且**不支持拉起exported为false的目标组件**。

## 跨设备启动约束总结

第三方应用进行跨设备组件启动时，受以下规则约束：

| 约束项 | 规则说明 |
| --- | --- |
| 设备可信关系 | 如果登录同一个华为账号，则设备间会进行自组网；非同账号环境下，需先通过[设备发现](../distributedservice/devicemanager-guidelines.md#设备发现开发指导)和[设备绑定](../distributedservice/devicemanager-guidelines.md#设备绑定开发指导)建立可信关系以完成组网，否则可信关系不满足将被拦截 |
| 应用状态 | 仅支持前台应用发起跨设备启动，后台应用发起将被拦截 |
| 目标可见性 | 仅支持拉起`exported`为`true`的目标组件（缺省值为`false`），缺省或配置为`false`时将被拦截 |
| 自定义权限 | 若目标组件在`module.json5`中声明了`permissions`，调用方需持有其中所有权限 |

## module.json5配置项说明

跨设备启动时，目标组件在`module.json5`中的以下配置项会影响启动结果。字段说明可参考[abilities标签](../quick-start/module-configuration-file.md#abilities标签)。

| 配置项 | 说明 | 跨设备启动影响 |
| --- | --- | --- |
| `exported` | 组件是否可被其他应用调用，**缺省值为`false`** | 若配置为`false`，调用方需申请`ohos.permission.START_INVISIBLE_ABILITY`权限方可拉起 |
| `permissions` | 组件被拉起时要求调用方持有的权限列表 | 若声明了权限数组，调用方必须持有其中所有权限，否则启动被拦截。权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md) |
| `type` | 组件类型（`UIAbility`或`ExtensionAbility`） | 决定可使用的启动接口 |

## 支持的启动接口

### UIAbility组件启动接口

第三方应用可通过以下接口跨设备启动 UIAbility 组件：

| 接口 | 说明 | 特殊限制 |
| --- | --- | --- |
| [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | 启动UIAbility | - |
| [startAbilityForResult()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startAbilityForResult) | 启动目标UIAbility，并在目标组件调用[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult)销毁时获取返回结果 | 结果返回时，发起方组件的`exported`属性也会被校验，必须为`true` |
| [startAbilityByCall()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | 启动目标UIAbility并将通信对象返回给发起方 | **仅支持同应用**跨设备调用，建立通路过程中底层软总线会校验双端应用的`ohos.permission.DISTRIBUTED_DATASYNC`权限。权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md) |

### ExtensionAbility组件启动接口

第三方应用可通过以下接口跨设备启动并连接 ExtensionAbility 组件：

| 接口 | 说明 | 特殊限制 |
| --- | --- | --- |
| [connectServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-serviceExtensionContext.md#serviceextensioncontextconnectserviceextensionability) | 连接ServiceExtensionAbility | 建立通路过程中底层软总线会校验双端应用的`ohos.permission.DISTRIBUTED_DATASYNC`权限。权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md) |

> **说明：**
>
> - startAbilityByCall场景不校验自定义权限，但会校验目标组件的可见性配置（结合设备安全等级）。若目标组件不可见且调用方设备安全等级低于被调用方设备，则拦截。
> - 禁止拉起`Distributed`类型的ExtensionAbility组件。

## 跨设备启动流程

启动 UIAbility 组件的具体校验流程如下图：

![component-startup-rules-cross-device](figures/component-startup-rules-cross-device.png)

## 跨设备启动流程

启动 UIAbility 组件的具体校验流程如下图：

![component-startup-rules-cross-device](figures/component-startup-rules-cross-device.png)
