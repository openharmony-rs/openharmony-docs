# AgentCard

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1630992de2f5af1dcca3ca27d11e23e0321182c9 translatedAt=2026-05-30T03:00:53.089Z pushedAt=2026-05-30T07:27:39.306Z -->

AgentCard is equivalent to the "business card" of an Agent (intelligent agent), used to describe the Agent's capabilities and skills. It is configured by the developer in the Agent's configuration file agent_config.json.

An Agent is an AgentExtensionAbility instance. Developers can obtain the AgentCard of the current AgentExtensionAbility through the agentCard property in AgentExtensionContext.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest version.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## AgentCard

Describes the basic information and abilities of an agent.

**Model Constraints:** This interface can be used only in the stage model.

**Atomic service API:** This interface is supported in atomic services since API version 24.

**System Capability:** SystemCapability.Ability.AgentRuntime.Core

| Name | Type | Read-only | Optional | Description |
| --------------------- | -------------------------------------------------------- | ---- | ---- | ------------------------------------------ |
| agentId | string | No | No | Unique identifier of the Agent. The agentId must be unique within the same application. |
| name | string | No | No | Name of the Agent. It is generally used by the consumer to display in the UI, for example, "Recipe Assistant". |
| description | string | No | No | Description of the Agent's functionality. This description should clearly explain the Agent's core functions and purposes, helping users understand what the Agent can do, for example, "Helps users search for recipes, plan menus, and provide cooking suggestions". |
| provider | [AgentProvider](#agentprovider) | No | Yes | Service provider information of the Agent, including the provider's organization name and official website URL, used to identify the source and copyright information of the Agent. |
| version | string | No | No | Version number of the Agent. It follows the Semantic Versioning specification (such as "1.0.0"), and the format is defined by the provider. The version number is used to identify functional iterations and compatibility changes of the Agent. |
| documentationUrl | string | No | Yes | URL of the Agent's documentation. Provides detailed Agent usage documentation, API descriptions, examples, and best practice guides to help developers better integrate and use the Agent. |
| capabilities | [AgentCapabilities](#agentcapabilities) | No | Yes | Set of optional capabilities supported by the Agent. Defines other optional capabilities supported by the Agent, such as streaming responses, push notifications, and status history queries. |
| defaultInputModes | Array\<string> | No | No | Set of input modes supported by the Agent across all [AgentSkill](#agentskill). Uses MIME type format to define supported input media types, for example, ["text/plain"] indicates plain text input, ["application/json"] indicates JSON structured data input, and ["image/png"] indicates image input. The inputModes at the [AgentSkill](#agentskill) level will override this default setting. |
| defaultOutputModes | Array\<string> | No | No | Set of output modes supported by the Agent across all [AgentSkill](#agentskill). Uses MIME type format to define supported output media types, for example, ["text/plain"] indicates plain text output, ["application/html"] indicates HTML format output, and ["application/json"] indicates JSON data output. The outputModes at the [AgentSkill](#agentskill) level will override this default setting. |
| skills | Array\<[AgentSkill](#agentskill)> | No | No | Set of functionalities provided by the Agent. Describes the specific functions or abilities that the Agent can perform. Each ability defines specific purposes, tags, and usage examples. The Agent must contain at least one ability. |
| iconUrl | string | No | No | URL of the Agent's icon. Provides a visual identifier icon for the Agent, used for display in the UI to enhance the Agent's recognizability and user experience. |
| category | string | No | No | Category of the Agent. Used for classifying and managing Agents. Common categories include: "productivity", "entertainment", "education", "finance", "health", etc. |
| extension | string | No | Yes | Extension configuration item of the Agent. Used to store custom extension configuration information, such as the Agent's opening remarks and version protocol number, in JSON string format. |
| appInfo | [AgentAppInfo](#agentappinfo) | No | No | Application information of the Agent. Contains identification information such as the bundle name, module name, and ability name of the application to which the Agent belongs, used to locate and manage the AgentExtensionAbility instance. |

## AgentProvider

Represents the service provider of the agent.

**Model Constraints:** This API can be used only in the Stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System Capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| organization     | string  | No   | No   | Organization name of the Agent provider. Identifies the company, organization, or individual that develops or provides the Agent. |
| url     | string  | No   | No   | URL of the Agent provider's website or related documentation. Provides an HTTPS link to the provider's official website, product page, or related documentation for users to learn more or get support. |

## AgentCapabilities

Defines optional capabilities supported by the Agent.

**Model Constraints:** This API can be used only in the stage model.

**Atomic service API:** Starting from API version 24, this API is supported in atomic services.

**System Capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| streaming     | boolean  | No   | Yes   | Whether the Agent supports streaming responses.<br>true: Indicates support for SSE (Server-Sent Events) streaming responses, allowing partial results to be returned in real time.<br>false: Indicates streaming is not supported; only complete results can be returned at once. After enabling streaming responses, the client can use the stream method to obtain real-time data streams. |
| pushNotifications     | boolean  | No   | Yes   | Whether the Agent supports sending push notifications for asynchronous task updates.<br>true: Indicates support. When the status of a long-running task changes (such as task completion, failure, or progress update), the Agent can actively push notifications to the client.<br>false: Indicates no support; the client needs to poll for task status. |
| stateTransitionHistory | boolean | No | Yes | Whether the Agent supports viewing task status change history.<br>true: Indicates support. The client can query the complete status transition record of a task from creation to completion (e.g., pending->running->completed).<br>false: Indicates status history query is not supported. |
| extendedAgentCard     | boolean  | No   | Yes   | Whether the Agent supports providing an extended AgentCard during authentication.<br>true: Indicates support. After passing authentication, the client can obtain an extended AgentCard containing additional information (such as private configurations, advanced capabilities).<br>false: Indicates only the basic AgentCard is provided. |
| extension     | string  | No   | Yes   | Protocol extensions supported by the Agent. Used to store custom extension capability configurations in JSON string format. It can contain protocol-level extension parameters and custom fields, as agreed upon by the developer and the Agent consumer. |

## AgentSkill

Represents the different abilities or functions that an Agent can perform.

**Model Constraints:** This interface can only be used in the stage model.

**Atomic service API:** Starting from API version 24, this interface is supported in atomic services.

**System Capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| id     | string  | No   | No   | Unique identifier of the AgentSkill, which must be unique within an AgentCard. It is recommended to use a semantically meaningful naming format (such as "route-planner" or "recipe-search") for precisely specifying the ability to use in API calls. |
| name     | string  | No   | No   | Name of the AgentSkill. Used for display in the UI, for example, "Route Planning" or "Recipe Search". |
| description     | string  | No   | No   | Detailed description of the AgentSkill. It should clearly explain the specific functions, applicable scenarios, and problems that the ability can solve, for example, "Helps users plan travel routes between two points, providing multiple transportation options and real-time traffic information." |
| tags     | Array\<string>  | No   | No   | Keyword tags describing the capabilities of the AgentSkill. Used for ability classification, retrieval, and recommendation, for example, ["maps", "routing", "navigation"] or ["cooking", "recipe", "food"]. Tags should be concise and easy for users to understand and search. |
| examples     | Array\<string>  | No   | Yes   | Example prompts or usage scenarios that the AgentSkill can handle. Providing specific examples helps users understand how to use the ability, for example, ["Plan a route from Shanghai to Beijing"]. |
| inputModes     | Array\<string>  | No   | Yes   | Input modes supported by the AgentSkill. Defined using the MIME type format, for example, ["text/plain"]. If not set, the defaultInputModes at the AgentCard level will be used. This field allows customizing input types for a specific ability, overriding the default settings. |
| outputModes     | Array\<string>  | No   | Yes   | Output modes supported by the AgentSkill. Defined using the MIME type format, for example, ["text/plain", "application/html", "video/mp4"]. If not set, the defaultOutputModes at the AgentCard level will be used. This field allows customizing output types for a specific ability, overriding the default settings. |
| extension     | string  | No   | Yes   | Extension configuration item for the AgentSkill. Used to store ability-level custom extension configurations in JSON string format, which can contain parameters and configuration information specific to the ability. |

## AgentAppInfo

Application information of the agent.

**Model Constraints:** This API can be used only in the stage model.

**Atomic service API:** This API is supported in atomic services since API version 24.

**System Capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| bundleName     | string  | No   | No   | Bundle name of the AgentExtensionAbility to which the Agent belongs. |
| moduleName     | string  | No   | No   | Module name of the AgentExtensionAbility to which the Agent belongs. |
| abilityName     | string  | No   | No   | Ability name of the AgentExtensionAbility to which the Agent belongs. |
| deviceTypes     | Array\<string>  | No   | Yes   | List of device types supported by the Agent. For the value range, see [deviceTypes](../../quick-start/module-configuration-file.md#devicetypes). |
| minAppVersion     | string  | No   | Yes   | Minimum application version required for the Agent to run. Uses the semantic versioning format (for example, "1.0.0") to specify the minimum application version required to run the Agent. Applications with a version lower than this will not be able to load and run the Agent properly. |