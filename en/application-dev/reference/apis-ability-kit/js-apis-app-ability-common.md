# @ohos.app.ability.common (Ability Common Module)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=aa0fb9ac9cb84f1c8f057e9ad47e9d44face8fc4 translatedAt=2026-09-03T10:10:24.519Z pushedAt=2026-09-05T10:47:30.366Z -->

The module provides pure type definitions for common capabilities within Ability Kit, including various context objects, callback interfaces, and data structures. It exports type declarations only and does not include any implementation logic or executable code.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## UIAbilityContext

type UIAbilityContext = _UIAbilityContext.default

Defines the context environment for the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md). It inherits from Context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_UIAbilityContext](js-apis-inner-application-uiAbilityContext.md).default | UIAbility component context. |

## AbilityStageContext

type AbilityStageContext = _AbilityStageContext.default

Defines the context environment for the [AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md). It inherits from Context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AbilityStageContext](js-apis-inner-application-abilityStageContext.md).default | AbilityStage component context. |

## ApplicationContext

type ApplicationContext = _ApplicationContext.default

Defines the application context. It inherits from Context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_ApplicationContext](js-apis-inner-application-applicationContext.md).default | Application context. |

## BaseContext

type BaseContext = _BaseContext.default

Defines the parent class of all context types.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_BaseContext](js-apis-inner-application-baseContext.md).default | Parent class of all contexts. |

## Context

type Context = _Context.default

Defines the context base class for the [stage model](../../application-models/ability-terminology.md#stage-model).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_Context](js-apis-inner-application-context.md).default | Base class of the context in the Stage model. |

## ExtensionContext

type ExtensionContext = _ExtensionContext.default

Defines the context environment for the [ExtensionAbility](../apis-ability-kit/js-apis-app-ability-extensionAbility.md). It inherits from Context.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_ExtensionContext](js-apis-inner-application-extensionContext.md).default | ExtensionAbility component context. |

## FormExtensionContext

type FormExtensionContext = _FormExtensionContext.default

Defines the context environment for the [FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md). It inherits from [ExtensionContext](./js-apis-inner-application-extensionContext.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_FormExtensionContext](../apis-form-kit/js-apis-inner-application-formExtensionContext.md).default | FormExtensionAbility component context. |

## VpnExtensionContext<sup>11+</sup>

type VpnExtensionContext = _VpnExtensionContext.default

Defines the context environment for the [VpnExtensionAbility](../apis-network-kit/js-apis-VpnExtensionAbility.md). It inherits from Context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_VpnExtensionContext](../apis-network-kit/js-apis-inner-application-VpnExtensionContext.md).default | Context of the VpnExtensionAbility component. |

## EventHub

type EventHub = _EventHub.default

Defines EventHub, which is an event communication mechanism based on the publish-subscribe pattern.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_EventHub](js-apis-inner-application-eventHub.md).default | Event communication mechanism provided by the system and implemented based on the publish-subscribe pattern. |

## PacMap

type PacMap = _PacMap

Defines the container of basic data types.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model constraint:**
This API can be used in both the stage model and the FA model since API version 11.

| Type| Description|
| --- | --- |
| [_PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap) | Container of basic data types.|

## AbilityResult

type AbilityResult = _AbilityResult

Defines the result code and data returned when a started ability is terminated.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AbilityResult](js-apis-inner-ability-abilityResult.md) | Result code and data returned when a started ability is terminated.|

## AbilityStartCallback<sup>11+</sup>

type AbilityStartCallback = _AbilityStartCallback

Defines the callback invoked to return the UIExtensionAbility startup result. It is usually used as an input parameter in [UIAbilityContext.startAbilityByType](js-apis-inner-application-uiAbilityContext.md#startabilitybytype11) or [UIExtensionContext.startAbilityByType](js-apis-app-ability-uiExtensionContentSession.md#startabilitybytype11).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AbilityStartCallback](js-apis-inner-application-abilityStartCallback.md) | Callback invoked to return the UIExtensionAbility startup result.|

## ConnectOptions

type ConnectOptions = _ConnectOptions

Defines the connection options. It is used as an input parameter for connection to a background service, to receive the connection status with the background service.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_ConnectOptions](js-apis-inner-ability-connectOptions.md) | Input parameter used to receive the connection status with the background service.|

## UIExtensionContext<sup>10+</sup>

type UIExtensionContext = _UIExtensionContext.default

Defines the context environment for the [UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md). It inherits from Context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_UIExtensionContext](js-apis-inner-application-uiExtensionContext.md).default | UIExtensionAbility component context. |

## EmbeddableUIAbilityContext<sup>12+</sup>

type EmbeddableUIAbilityContext = _EmbeddableUIAbilityContext.default

Defines the context environment for the [EmbeddableUIAbility](../apis-ability-kit/js-apis-app-ability-embeddableUIAbility.md). It inherits from Context.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_EmbeddableUIAbilityContext](js-apis-inner-application-EmbeddableUIAbilityContext.md).default | EmbeddableUIAbility component context. |

## PhotoEditorExtensionContext<sup>12+</sup>

type PhotoEditorExtensionContext = _PhotoEditorExtensionContext.default

Defines the context environment for the [PhotoEditorExtensionAbility](../apis-ability-kit/js-apis-app-ability-photoEditorExtensionAbility.md). It inherits from Context.

**System capability**: SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_PhotoEditorExtensionContext](js-apis-app-ability-photoEditorExtensionContext.md).default | Component context of PhotoEditorExtensionAbility. |

## UIServiceProxy<sup>14+</sup>

type UIServiceProxy = _UIServiceProxy.default

Defines the capability for data communication with the UIServiceExtensionAbility. UIServiceExtensionAbility is a special type of ExtensionAbility provided by the system and is used to provide extended capabilities related to floating windows.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_UIServiceProxy](js-apis-inner-application-uiserviceproxy.md).default | Provides the capability of data communication with the UIServiceExtensionAbility server. |

## UIServiceExtensionConnectCallback<sup>14+</sup>

type UIServiceExtensionConnectCallback = _UIServiceExtensionConnectCallback.default

Defines the connection callback. It is used as an input parameter for connection to a UIServiceExtensionAbility, to provide the callback for the connection.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_UIServiceExtensionConnectCallback](js-apis-inner-application-uiServiceExtensionconnectcallback.md).default | Provides the capability of UIServiceExtensionAbility connection callback data. |

## AppServiceExtensionContext<sup>20+</sup>

type AppServiceExtensionContext = _AppServiceExtensionContext.default

Defines the context environment for the [AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md). It inherits from Context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_AppServiceExtensionContext](js-apis-inner-application-appServiceExtensionContext.md).default | Component context of AppServiceExtensionAbility. |

## FormEditExtensionContext<sup>22+</sup>

type FormEditExtensionContext = _FormEditExtensionContext.default

Defines the context environment for the [FormEditExtensionAbility](../apis-form-kit/js-apis-app-form-formEditExtensionAbility.md). It inherits from [UIExtensionContext](./js-apis-inner-application-uiExtensionContext.md).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Ability.Form

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_FormEditExtensionContext](../apis-form-kit/js-apis-inner-application-formEditExtensionContext.md).default | Component context of FormEditExtensionAbility. |

## LiveFormExtensionContext<sup>22+</sup>

type LiveFormExtensionContext = _LiveFormExtensionContext.default

Defines the context environment for the [LiveFormExtensionAbility](../apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md). It inherits from [ExtensionContext](./js-apis-inner-application-extensionContext.md).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Ability.Form

**Model restriction**: This API can be used only in the stage model.

| Type| Description|
| --- | --- |
| [_LiveFormExtensionContext](../apis-form-kit/js-apis-application-LiveFormExtensionContext.md).default | Component context of LiveFormExtensionAbility. |

## AgentCard<sup>24+</sup>

type AgentCard = _AgentCard

[AgentCard](../apis-ability-kit/js-apis-inner-application-AgentCard.md) is equivalent to the "business card" of an Agent, used to describe the capabilities and skills of the Agent. It is configured by the developer in the agent_config.json configuration file of the Agent.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentCard](../apis-ability-kit/js-apis-inner-application-AgentCard.md) | The "business card" of an Agent, used to describe the capabilities and skills of the Agent. |

## AgentProvider<sup>24+</sup>

type AgentProvider = _AgentProvider

[AgentProvider](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentprovider) indicates the service provider of an Agent.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentProvider](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentprovider) | Service provider of an Agent. |

## AgentCapabilities<sup>24+</sup>

type AgentCapabilities = _AgentCapabilities

[AgentCapabilities](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentcapabilities) defines the optional capabilities supported by an Agent.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentCapabilities](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentcapabilities) | Defines the optional capabilities supported by an agent. |

## AgentSkill<sup>24+</sup>

type AgentSkill = _AgentSkill

[AgentSkill](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentskill) indicates the different capabilities or functions that an Agent can perform.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentSkill](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentskill) | Represents the different capabilities or functions that an agent can perform. |

## AgentAppInfo<sup>24+</sup>

type AgentAppInfo = _AgentAppInfo

[AgentAppInfo](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentappinfo) indicates the application information of the agent to which the Agent belongs.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentAppInfo](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentappinfo) | Application information of the agent to which the Agent belongs. |

## AgentHostProxy<sup>24+</sup>

type AgentHostProxy = _AgentHostProxy

[AgentHostProxy](../apis-ability-kit/js-apis-inner-application-agentHostProxy.md) is used to send data or security authentication requests from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server to the client.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentHostProxy](../apis-ability-kit/js-apis-inner-application-agentHostProxy.md) | Used to send data or security authentication requests from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server to the client. |

## AgentExtensionContext<sup>24+</sup>

type AgentExtensionContext = _AgentExtensionContext

[AgentExtensionContext](../apis-ability-kit/js-apis-inner-application-agentExtensionContext.md) is the context of [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md), and inherits from [ExtensionContext](js-apis-inner-application-extensionContext.md).

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentExtensionContext](../apis-ability-kit/js-apis-inner-application-agentExtensionContext.md) | The context of [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md), which inherits from [ExtensionContext](js-apis-inner-application-extensionContext.md). |

**Example**

```ts
import { common } from '@kit.AbilityKit';

let uiAbilityContext: common.UIAbilityContext;
let abilityStageContext: common.AbilityStageContext;
let applicationContext: common.ApplicationContext;
let baseContext: common.BaseContext;
let context: common.Context;
let uiExtensionContext: common.UIExtensionContext;
let extensionContext: common.ExtensionContext;
let formExtensionContext: common.FormExtensionContext;
let vpnExtensionContext: common.VpnExtensionContext;
let eventHub: common.EventHub;
let pacMap: common.PacMap;
let abilityResult: common.AbilityResult;
let abilityStartCallback: common.AbilityStartCallback;
let connectOptions: common.ConnectOptions;
let embeddableUIAbilityContext: common.EmbeddableUIAbilityContext;
let photoEditorExtensionContext: common.PhotoEditorExtensionContext;
let uiServiceProxy : common.UIServiceProxy;
let uiServiceExtensionConnectCallback : common.UIServiceExtensionConnectCallback;
let appServiceExtensionContext : common.AppServiceExtensionContext;
let formEditExtensionContext : common.FormEditExtensionContext;
let liveFormExtensionContext : common.LiveFormExtensionContext;
let agentCard: common.AgentCard;
let agentProvider: common.AgentProvider;
let agentCapabilities: common.AgentCapabilities;
let agentSkill: common.AgentSkill;
let agentAppInfo: common.AgentAppInfo;
let agentHostProxy: common.AgentHostProxy;
let agentExtensionContext: common.AgentExtensionContext;
```
