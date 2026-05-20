# 设备内组件启动规则（Stage模型）（仅对系统应用开放）

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

为了保障系统安全与用户体验，系统限制了应用在后台状态时任意弹窗、相互唤醒以及前台应用任意跳转的行为，相关行为表现请参考[设备内组件启动规则（Stage模型）](./component-startup-rules-inner-device.md)。本文主要介绍系统应用在设备内启动[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)的约束规则。

> **说明：**
> 
> 组件启动规则自API version 9开始生效，新增规则生效版本在规则中单独说明。开发者需熟知组件启动规则，以避免业务功能异常。

## 前后台应用启动

   位于后台状态的UIAbility应用，默认不允许再启动UIAbility组件。可申请ohos.permission.START_ABILITIES_FROM_BACKGROUND（下文简称BACKGROUND）权限启动UIAbility组件，权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md)。

   | 应用状态 | 权限要求   |
   | -------- | ---------- |
   | 前台应用 | 无         |
   | 后台应用 | BACKGROUND |

   > **说明：**
   >
   > - 对于2in1和Tablet设备：
   >   - 从API version 18开始，如果应用已创建在前台显示的悬浮窗，可不受该条规则约束。
   >   - 从API version 21开始，如果应用自身已经添加到状态栏，可不受该条规则约束。

## 跨应用启动

   通过[startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability)/[openLink()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)等跨应用启动UIAbility组件时，只允许拉起exported为true的目标组件。若申请ohos.permission.START_INVISIBLE_ABILITY（下文简称INVISIBLE）权限，可不受该条规则约束，权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md)。

   | 应用状态 | 组件可见性     | 权限要求                       |
   | -------- | -------------- | ----------------------------- |
   | 前台应用 | exported:true  | 无                             |
   | 前台应用 | exported:false | INVISIBLE权限                  |
   | 后台应用 | exported:true  | BACKGROUND权限                 |
   | 后台应用 | exported:false | BACKGROUND权限 + INVISIBLE权限 |

   > **说明：**
   >
   > - 在module.json5配置文件中，每个UIAbility都有一个exported属性。exported字段说明可参考[abilities标签](../quick-start/module-configuration-file.md#abilities标签)。
   > - 目标组件exported字段配置为true，表示可以被其他应用调用。
   > - 目标组件exported字段配置为false，表示组件仅允许应用内启动。

   启动组件的具体校验流程如下图：

   ![component-startup-rules-inner-device-sys](figures/component-startup-rules-inner-device-sys.png)


   通过[startAbilityByCall()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall)接口跨应用启动UIAbility组件时，需要具备两个条件：1.申请ohos.permission.ABILITY_BACKGROUND_COMMUNICATION（下文简称CALL）权限，权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md)；2.目标UIAbility组件的exported为true，若申请ohos.permission.START_INVISIBLE_ABILITY（下文简称INVISIBLE）权限，可不受该条规则约束，权限的申请方式请参考[声明权限](../security/AccessToken/declare-permissions.md)。

   | 应用状态 | 组件可见性     | 权限要求                                  |
   | -------- | -------------- | ----------------------------------------- |
   | 前台应用 | exported:true  | CALL权限                                  |
   | 前台应用 | exported:false | INVISIBLE权限 + CALL权限                  |
   | 后台应用 | exported:true  | BACKGROUND权限 + CALL权限                 |
   | 后台应用 | exported:false | BACKGROUND权限 + INVISIBLE权限 + CALL权限 |

   启动组件的具体校验流程如下图：

   ![component-startup-rules-inner-device-call-sys](figures/component-startup-rules-inner-device-call-sys.png)
