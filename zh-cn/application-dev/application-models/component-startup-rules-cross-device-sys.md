# 跨设备组件启动规则（Stage模型）（仅对系统应用开放）

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @HelloCrease-->

本文介绍系统应用跨设备启动[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)和[ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)的约束规则。第三方应用规则请参考[跨设备组件启动规则（Stage模型）](./component-startup-rules-cross-device.md)。

> **说明：**
> - 系统应用支持申请后台启动权限（`ohos.permission.START_ABILITIES_FROM_BACKGROUND`）和拉起不可见组件权限（`ohos.permission.START_INVISIBLE_ABILITY`），权限申请方式参考[声明权限](../security/AccessToken/declare-permissions.md)。
> - 跨设备启动需设备间建立可信关系（同账号自组网或非同账号设备发现绑定），且目标设备在线。

## 支持的启动接口

### UIAbility组件启动接口

系统应用可通过以下接口跨设备启动 UIAbility 组件：

| 接口 | 说明 | 特殊限制 |
| --- | --- | --- |
| [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | 启动UIAbility | 若调用方位于后台，需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限 |
| [startAbilityForResult()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startAbilityForResult) | 启动目标UIAbility，并在目标组件调用[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult)销毁时获取返回结果 | 结果返回时，发起方组件的`exported`属性也会被校验，必须为`true` |
| [startAbilityByCall()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | 启动目标UIAbility并将通信对象返回给发起方 | **仅支持同应用**跨设备调用，建立通路过程中底层软总线会校验双端应用的`ohos.permission.DISTRIBUTED_DATASYNC`权限 |

### ExtensionAbility组件启动接口

系统应用可通过以下接口跨设备启动并连接 ExtensionAbility 组件：

| 接口 | 说明 | 特殊限制 |
| --- | --- | --- |
| [connectServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-serviceExtensionContext.md#serviceextensioncontextconnectserviceextensionability) | 连接ServiceExtensionAbility | 若调用方位于后台，需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限；建立通路过程中底层软总线会校验双端应用的`ohos.permission.DISTRIBUTED_DATASYNC`权限 |

## 跨设备启动流程

启动 UIAbility 组件的具体校验流程如下图：

![component-startup-rules-cross-device-sys](figures/component-startup-rules-cross-device-sys.png)
