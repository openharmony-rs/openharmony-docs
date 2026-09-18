# @ohos.app.ability.common(Ability Common Module)

You can use this module to reference the ability public module class.

**Since:** 9

**Model restriction:** 
- API version 11 and later: This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { common } from '@kit.AbilityKit';
```

## Summary

### Types

| Name | Description |
| --- | --- |
| [AbilityResult](arkts-ability-common-abilityresult-t.md) | Defines the result code and data returned when a started ability is terminated. |
| [AbilityStageContext](arkts-ability-common-abilitystagecontext-t.md) | Defines the context environment for the [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md). It inherits from Context. |
| [AbilityStartCallback](arkts-ability-common-abilitystartcallback-t.md) | Defines the callback invoked to return the UIExtensionAbility startup result. It is usually used as an input parameter in [UIAbilityContext.startAbilityByType](arkts-ability-uiabilitycontext-c.md#startabilitybytype) or [UIExtensionContext.startAbilityByType](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#startabilitybytype). |
| [AgentAppInfo](arkts-ability-common-agentappinfo-t.md) | Application-related information for the agent. |
| [AgentCapabilities](arkts-ability-common-agentcapabilities-t.md) | Capabilities in an AgentCard represent the specific skills, services, and functions that an agent can perform or provide within the system. |
| [AgentCard](arkts-ability-common-agentcard-t.md) | The AgentCard information describes the basic information and capabilities provided by an Agent. |
| [AgentExtensionContext](arkts-ability-common-agentextensioncontext-t.md) | The context of the agent service ability. |
| [AgentHostProxy](arkts-ability-common-agenthostproxy-t.md) | The AgentHostProxy is a proxy object for the client connected to the Agent, through which it can communicate with the Agent's connection counterpart. |
| [AgentProvider](arkts-ability-common-agentprovider-t.md) | The Provider in an AgentCard refers to the organization or platform that issues and manages the agent's credentials. |
| [AgentSkill](arkts-ability-common-agentskill-t.md) | Skills in an AgentCard represent the specific abilities, expertise, and proficiencies that an agent possesses for performing tasks or solving problems. |
| [ApplicationContext](arkts-ability-common-applicationcontext-t.md) | Defines the application context. It inherits from Context. |
| [AppServiceExtensionContext](arkts-ability-common-appserviceextensioncontext-t.md) | Defines the context environment for the [AppServiceExtensionAbility](../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md). It inherits from Context. |
| [BaseContext](arkts-ability-common-basecontext-t.md) | Defines the parent class of all context types. |
| [ConnectOptions](arkts-ability-common-connectoptions-t.md) | Defines the connection options. It is used as an input parameter for connection to a background service, to receive the connection status with the background service. |
| [Context](arkts-ability-common-context-t.md) | Defines the context base class for the [stage model](../../../application-models/ability-terminology.md#stage-model). |
| [EmbeddableUIAbilityContext](arkts-ability-common-embeddableuiabilitycontext-t.md) | Defines the context environment for the [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md). It inherits from Context. |
| [EventHub](arkts-ability-common-eventhub-t.md) | Defines EventHub, which is an event communication mechanism based on the publish-subscribe pattern. |
| [ExtensionContext](arkts-ability-common-extensioncontext-t.md) | Defines the context environment for the [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md). It inherits from Context. |
| [FormEditExtensionContext](arkts-ability-common-formeditextensioncontext-t.md) | The context of form edit extension. It allows access to formEditExtension-specific resources. |
| [FormExtensionContext](arkts-ability-common-formextensioncontext-t.md) | The context of form extension. It allows access to formExtension-specific resources. |
| [LiveFormExtensionContext](arkts-ability-common-liveformextensioncontext-t.md) | The context of live form extension. It allows access to liveFormExtension-specific resources. |
| [PacMap](arkts-ability-common-pacmap-t.md) | Defines the container of basic data types. |
| [PhotoEditorExtensionContext](arkts-ability-common-photoeditorextensioncontext-t.md) | The context of an photo editor extension ability. |
| [UIAbilityContext](arkts-ability-common-uiabilitycontext-t.md) | Defines the context environment for the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md). It inherits from Context. |
| [UIExtensionContext](arkts-ability-common-uiextensioncontext-t.md) | Defines the context environment for the [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md). It inherits from Context. |
| [UIServiceExtensionConnectCallback](arkts-ability-common-uiserviceextensionconnectcallback-t.md) | Defines the connection callback. It is used as an input parameter for connection to a UIServiceExtensionAbility, to provide the callback for the connection. |
| [UIServiceProxy](arkts-ability-common-uiserviceproxy-t.md) | Defines the capability for data communication with the UIServiceExtensionAbility. UIServiceExtensionAbility is a special type of ExtensionAbility provided by the system and is used to provide extended capabilities related to floating windows. |
| [VpnExtensionContext](arkts-ability-common-vpnextensioncontext-t.md) | The context of vpn extension. It allows access to vpnExtension-specific resources. The class of auto startup info. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AgentExtensionConnectCallback](arkts-ability-common-agentextensionconnectcallback-t-sys.md) | Represents the AgentExtensionConnectCallback type. |
| [AgentProxy](arkts-ability-common-agentproxy-t-sys.md) | Represents the AgentProxy type. |
| [AutoFillExtensionContext](arkts-ability-common-autofillextensioncontext-t-sys.md) | Level-2 module AutoFillExtensionContext. |
| [AutoStartupCallback](arkts-ability-common-autostartupcallback-t-sys.md) | Level-2 module AutoStartupCallback. |
| [AutoStartupInfo](arkts-ability-common-autostartupinfo-t-sys.md) | Level-2 module AutoStartupInfo. |
| [CliToolEvent](arkts-ability-common-clitoolevent-t-sys.md) | The event data of cli execute. |
| [FunctionInfo](arkts-ability-common-functioninfo-t-sys.md) | Describes the basic information of a function. |
| [ServiceExtensionContext](arkts-ability-common-serviceextensioncontext-t-sys.md) | Level-2 module ServiceExtensionContext. |
| [ToolEventCallback](arkts-ability-common-tooleventcallback-t-sys.md) | Define the cli event callback function. |
| [ToolInfo](arkts-ability-common-toolinfo-t-sys.md) | Define basic information about the CLI tool. |
| [ToolSummary](arkts-ability-common-toolsummary-t-sys.md) | Define basic summary information about the CLI tool. |
| [UIServiceExtensionContext](arkts-ability-common-uiserviceextensioncontext-t-sys.md) | Level-2 module UIServiceExtensionContext. |
| [UIServiceHostProxy](arkts-ability-common-uiservicehostproxy-t-sys.md) | Level-2 module UIServiceHostProxy. |
<!--DelEnd-->
