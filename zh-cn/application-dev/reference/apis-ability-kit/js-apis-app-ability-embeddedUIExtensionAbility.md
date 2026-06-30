# @ohos.app.ability.EmbeddedUIExtensionAbility (支持跨进程界面嵌入的ExtensionAbility组件)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

EmbeddedUIExtensionAbility为开发者提供了跨进程界面嵌入的能力，继承自[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md)。

开发者通过实现EmbeddedUIExtensionAbility，为本应用提供跨进程界面嵌入能力。例如，开发者可以在[UIAbility](js-apis-app-ability-uiAbility.md)的页面中通过[EmbeddedComponent](../apis-arkui/arkui-ts/ts-container-embedded-component.md)嵌入本应用的EmbeddedUIExtensionAbility提供的界面。

各类Ability的继承关系详见[继承关系说明](./js-apis-app-ability-ability.md#ability的继承关系说明)。

> **说明：**
>
> 本模块首批接口从API version 12 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { EmbeddedUIExtensionAbility } from '@kit.AbilityKit';
```

## EmbeddedUIExtensionAbility

EmbeddedUIExtensionAbility为开发者提供了跨进程界面嵌入的能力，继承自[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md)。

目前EmbeddedUIExtensionAbility只能被同应用的UIAbility拉起，从API版本26.0.0开始，如果EmbeddedComponent所属应用申请了ohos.permission.SUPPORT_CROSS_APP_EMBED_FOR_OA权限（该权限仅企业普通应用可申请），且该应用的[appIdentifier](../../quick-start/common-problem-of-application.md#什么是appidentifier)在EmbeddedUIExtensionAbility支持的应用清单（即[extensionAbilities标签](../../quick-start/module-configuration-file.md#extensionabilities标签)的appIdentifierAllowList属性）中，则允许EmbeddedComponent跨应用拉起EmbeddedUIExtensionAbility。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**设备行为差异**：
- 从API version 12开始，该接口在Tablet中可正常调用，在其他设备类型中无法被启动。
- 从API version 13开始，该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中无法被启动。
- 从API version 23开始，该接口在PC/2in1、Tablet、Car中可正常调用，在其他设备类型中无法被启动。