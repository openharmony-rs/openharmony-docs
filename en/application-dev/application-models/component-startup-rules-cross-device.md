# Cross-Device Component Startup Rules

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=f7c29098b44cb73061ff88489a733c53b3a07980 translatedAt=2026-11-02T13:31:54.737Z pushedAt=2026-11-03T06:38:34.827Z nl=1 -->

In cross-device collaboration scenarios, applications often need to start [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) or [ExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md) components on other devices to implement multi-device interaction. Cross-device startup involves multiple constraints such as device trust relationships, security level matching, and permission verification. Failure to meet these rules will cause startup to fail. This document sorts out the complete rules for cross-device component startup, covering collaboration interface selection, startup conditions, and verification processes. It is intended for developers to reference when implementing cross-device component startup and multi-device collaboration, so as to standardize interface calls and quickly locate startup exceptions.

## Basic Concepts

- **Multi-round Interaction**: After the startup party and the target party components establish a connection, multiple rounds of data communication and business interaction can be performed.
- **Single Interaction**: After the startup party starts the target party component, it only obtains the startup result or the result returned when the target party is destroyed, with no subsequent multi-round communication.
- **Device Security Level**: A level divided based on device security capabilities (for example, TEE, secure storage chips, etc.). The higher the level, the stronger the security capability. For details, see [Device Security Level](../database/native-access-control-by-device-and-data-level.md#device-security-levels).

## Collaborative Interfaces

| Category | Interface | Applicable Scenarios |
| --- | --- | --- |
| Multi-round Interaction | [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | Supports cross-device startup of UIAbility components. It is recommended to use this interface first, as it provides faster collaborative connection and better transmission performance. For details, see [Cross-Device UIAbility Connection Development Guide](../distributedservice/abilityconnectmanager-guidelines.md). |
| Multi-round Interaction | [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | Supports cross-device startup of ExtensionAbility components. |
| Multi-round Interaction | [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | Supports cross-device startup of UIAbility components within the same application (same APPID). |
| Single Interaction | [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | Supports single interaction for cross-device startup of UIAbility components, returning only the startup result. |
| Single Interaction | [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | Supports single interaction for cross-device startup of UIAbility components, and supports returning detailed results when the target party component calls terminateSelfWithResult to destroy itself. |

## Startup Conditions

To start a component across devices, the following three requirements must be met simultaneously:

1. Trust relationship between devices

   - Both devices are logged in to the same account, satisfying the trust relationship requirement.
   - If the two devices use different accounts, a trust relationship must be established in advance through [Device Discovery](../distributedservice/devicemanager-guidelines.md#discovering-devices) and [Device Binding](../distributedservice/devicemanager-guidelines.md#binding-a-device).

2. Distributed device security level requirement

   This depends on the `exported` configuration value of the target party's component under the abilities tag in the [module.json5](../quick-start/module-configuration-file.md) file:

   - `false` (default value): the device security level of the startup party must be ≥ the device security level of the target party, and the startup party and the target party must be the same application (same APPID).
   - `true`: no security level requirement.

3. Application permission requirement

| Interface | Permission requirements of the target party on the startup party | Distributed collaboration-related permission requirements between the startup party and the target party |
| --- | --- | --- |
| [abilityConnectionManager](../reference/apis-distributedservice-kit/js-apis-distributed-abilityConnectionManager.md) | If the target party configures `permissions` under the abilities tag in the module.json5 file, the startup party must hold all of them. | ohos.permission.DISTRIBUTED_DATASYNC<br>ohos.permission.GET_NETWORK_INFO<br>ohos.permission.SET_NETWORK_INFO<br>ohos.permission.INTERNET |
| [connectServiceExtensionAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) | If the target party configures `permissions` under the abilities tag in the module.json5 file, the startup party must hold all of them. | ohos.permission.DISTRIBUTED_DATASYNC |
| [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) | No requirement (only for calls within the same application). | ohos.permission.DISTRIBUTED_DATASYNC |
| [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) | If the target party configures `permissions` under the abilities tag in the module.json5 file, the startup party must hold all of them. | No requirement (single interaction only). |
| [startAbilityForResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilityforresult)<br>[terminateSelfWithResult](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) | If the target party configures `permissions` under the abilities tag in the module.json5 file, the startup party must hold all of them. | No requirement (single interaction only). |

> **Note**
>
> - For how to request permissions, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).
> - The ohos.permission.DISTRIBUTED_DATASYNC permission required by connectServiceExtensionAbility and startAbilityByCall is not verified during application startup; it is verified by the soft bus only when a connection is established between applications.
