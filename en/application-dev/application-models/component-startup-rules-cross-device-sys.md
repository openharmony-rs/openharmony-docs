# Cross-Device Component Startup Rules (System Applications Only)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=845e76a721ee369f099a0ff1bc6aa99a4726cad4 translatedAt=2026-11-02T13:54:39.318Z pushedAt=2026-11-03T07:00:33.072Z nl=1 -->

In cross-device collaboration scenarios, system applications often need to start [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) or [ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md) components on other devices to implement multi-device interaction. Cross-device startup involves multiple constraints such as device trust relationships, security level matching, and permission verification. Failure to meet the rules will cause the startup to fail. This document sorts out the complete rules for system applications to start components across devices, covering collaboration interface selection, startup conditions, and permission requirements. It is intended for system application developers to reference when implementing cross-device component startup and multi-device collaboration.

## Basic Concepts

- **Multi-round Interaction**: After the startup party establishes a connection with the target party's component, multiple rounds of data communication and business interaction can be performed.
- **Single-round Interaction**: After the startup party starts the target party's component, it only obtains the startup result or the result returned when the target party is destroyed, with no subsequent multi-round communication.
- **Device Security Level**: A level divided based on the device's security capabilities (for example, TEE, secure storage chip, etc.). The higher the level, the stronger the security capability. For details, see [Device Security Level](../database/native-access-control-by-device-and-data-level.md#device-security-levels).

## Collaborative Interfaces

| Classification | Interface | Applicable Scenarios |
| --- | --- | --- |
| Multi-round Interaction | [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | Supports cross-device startup of UIAbility components. It is recommended to use this interface first, as it provides faster collaborative connection and better transmission performance. For details, see [Cross-Device UIAbility Connection Development Guide](../distributedservice/abilityconnectmanager-guidelines.md). |
| Multi-round Interaction | [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | Supports cross-device startup of ExtensionAbility components. |
| Multi-round Interaction | [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | Supports cross-device startup of UIAbility components and multi-round interaction. |
| Single-round Interaction | [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | Supports single-round interaction for cross-device startup of UIAbility components, returning only the startup result. |
| Single-round Interaction | [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | Supports single-round interaction for cross-device startup of UIAbility components, and supports returning detailed results when the target party component calls terminateSelfWithResult to destroy itself. |

## Startup Conditions

Cross-device component startup must meet all of the following four requirements:

1. Trust relationship requirement between devices

   - Both devices are logged in to the same account, satisfying the trust relationship requirement.
   - If the two devices use different accounts, a trust relationship must be established in advance through [Device Discovery](../distributedservice/devicemanager-guidelines.md#discovering-devices) and [Device Binding](../distributedservice/devicemanager-guidelines.md#binding-a-device).

2. Application startup state requirement

   Depends on the foreground/background state of the startup party's application:

   - For a foreground application, there is no permission requirement.
   - For a background application, ohos.permission.START_ABILITIES_FROM_BACKGROUND must be applied for before the target component can be started.

3. Distributed device security level requirement

   Depends on the `exported` configuration value of the abilities label of the target component in the [module.json5](../quick-start/module-configuration-file.md) file:

   - `false` (default value), requires that the device security level of the startup party be ≥ the device security level of the target party.
   - `true`, no security level requirement.

4. Application permission requirements

| Interface | Permission requirements of the target party on the startup party | Distributed collaboration-related permission requirements of the startup party and the target party |
| --- | --- | --- |
| [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | If the target party configures `permissions` of the abilities label in the module.json5 file, the startup party must hold all of these permissions.<br>If the target party configures exported as false in the module.json5 file, the ohos.permission.START_INVISIBLE_ABILITY permission needs to be applied for. | ohos.permission.DISTRIBUTED_DATASYNC<br>ohos.permission.GET_NETWORK_INFO<br>ohos.permission.SET_NETWORK_INFO<br>ohos.permission.INTERNET |
| [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | If the target party configures `permissions` of the abilities label in the module.json5 file, the startup party must hold all of these permissions.<br>If the target party configures exported as false in the module.json5 file, the ohos.permission.START_INVISIBLE_ABILITY permission needs to be applied for. | ohos.permission.DISTRIBUTED_DATASYNC |
| [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | No requirement (only for calls within the same application). | ohos.permission.DISTRIBUTED_DATASYNC |
| [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | If the target party configures `permissions` of the abilities label in the module.json5 file, the startup party must hold all of these permissions.<br>If the target party configures exported as false in the module.json5 file, the ohos.permission.START_INVISIBLE_ABILITY permission needs to be applied for. | No requirement (single-round interaction only). |
| [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | If the target party configures `permissions` of the abilities label in the module.json5 file, the startup party must hold all of these permissions.<br>If the target party configures exported as false in the module.json5 file, the ohos.permission.START_INVISIBLE_ABILITY permission needs to be applied for. | No requirement (single-round interaction only). |

> **Note**
>
> - For how to apply for permissions, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).
> - The ohos.permission.DISTRIBUTED_DATASYNC permission required by connectServiceExtensionAbility and startAbilityByCall is not verified during the application startup phase; it is verified by the soft bus only during the connection establishment between applications.
