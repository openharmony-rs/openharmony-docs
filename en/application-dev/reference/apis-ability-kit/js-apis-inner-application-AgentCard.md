# AgentCard
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=26a16dc945092dac2fe460e6fbd5bf509ffa8caa translatedAt=2026-09-03T11:38:48.425Z pushedAt=2026-09-05T10:47:30.670Z -->

AgentCard is the "business card" of an Agent, used to describe the capabilities and skills of the Agent. It is configured by the developer in the Agent configuration file agent_config.json.

An Agent is an AgentExtensionAbility instance. The developer can obtain the AgentCard of the current AgentExtensionAbility through the agentCard property in AgentExtensionContext.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## AgentCard

Describes the basic information and capabilities of an agent.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name                  | Type                                                     | Read-only | Optional | Description                                      |
| --------------------- | -------------------------------------------------------- | ---- | ---- | ------------------------------------------ |
| agentId | string | No | No | Unique identifier of the Agent. Within the same application, agentId cannot be duplicated. |
| name        | string   | No   | No   | Name of the Agent. It is generally displayed to users in the UI, for example, "Recipe Assistant". |
| description | string   | No   | No   | Describes the core functions, purposes, and applicable scenarios of the Agent, for example, "Helps users search for recipes, plan menus, and provide cooking suggestions". |
| type  | [agentConstant.AgentCardType](js-apis-app-agent-agentConstant.md#agentconstantagentcardtype) | No | Yes | Type of the AgentCard. <!--Del-->When the enum value of [agentConstant.AgentCardType](js-apis-app-agent-agentConstant-sys.md#agentconstantagentcardtype) is LOW_CODE, the corresponding application must be a system application; otherwise, the Agent card cannot be registered, installed, or updated. <!--DelEnd-->If not specified, the default type is APP. <br>**Since:** 26.0.0 <br>**Atomic service API:** Since API version 26.0.0, this API is supported in atomic services. |
| provider | [AgentProvider](#agentprovider) | No | Yes | Service provider information of the Agent, including the organization name and official website URL of the provider, used to identify the source and copyright information of the Agent. If not configured, no provider information is included. |
| version | string | No | No | Version number of the Agent. It follows the semantic versioning specification (for example, "1.0.0"), and the format is defined by the provider. The version number is used to identify the feature iteration and compatibility changes of the Agent. |
| documentationUrl           | string                                                   | No   | Yes   | URL of the Agent documentation. It provides detailed Agent usage documentation, API descriptions, examples, and best practice guides to help developers better integrate and use the Agent. If not configured, no documentation link is provided. |
| capabilities             | [AgentCapabilities](#agentcapabilities)                                          | No   | Yes   | Set of optional capabilities supported by the Agent. Defines other optional capabilities supported by the Agent, such as streaming responses, push notifications, and status history queries. If not configured, no additional capabilities are enabled. |
| defaultInputModes | Array\<string> | No | No | Set of input modes supported by the Agent across all [AgentSkill](#agentskill) instances. Uses the MIME type format to define the supported input media types, for example, ["text/plain"] indicates plain text input, ["application/json"] indicates JSON structured data input, and ["image/png"] indicates image input. The inputModes at the [AgentSkill](#agentskill) level override this default setting. |
| defaultOutputModes           | Array\<string>                                                   | No   | No   | Set of output modes supported by the Agent across all [AgentSkill](#agentskill) instances. Uses the MIME type format to define the supported output media types, for example, ["text/plain"] indicates plain text output, ["application/html"] indicates HTML format output, and ["application/json"] indicates JSON data output. The outputModes at the [AgentSkill](#agentskill) level override this default setting. |
| skills               | Array\<[AgentSkill](#agentskill)>                                           | No   | No   | Set of functions provided by the Agent. Describes the specific functions or skills that the Agent can perform. Each skill defines its specific purpose, tags, and usage examples. The Agent must contain at least one skill. |
| iconUrl       | string                                                   | No   | No   | URL of the Agent icon. Provides a visual identification icon for the Agent, used for display in the UI to enhance the recognizability and user experience of the Agent.<br>**Note:** The system does not verify the content of this field. The caller must verify the validity and security of iconUrl. |
| category       | string                                                   | No   | No   | Category of the Agent. Used to classify and manage Agents. Common categories include "productivity", "entertainment", "education", "finance", and "health". |
| extension       | string                                                   | No   | Yes   | Extension configuration item of the Agent. Used to store custom extension configuration information, such as the Agent opening remarks and version protocol number, in JSON string format. If not configured, no extension configuration is used. |
| appInfo       | [AgentAppInfo](#agentappinfo)                                                   | No   | No   | Information about the application to which the Agent belongs. Contains identification information such as the bundle name, module name, and ability name of the application to which the Agent belongs, used to locate and manage the AgentExtensionAbility instance. |

## AgentProvider

Represents the service provider of an Agent.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| organization     | string  | No   | No   | Organization name of the Agent provider. Identifies the developer or provider (company, organization, or individual) of the Agent. |
| url     | string  | No   | No   | URL of the Agent provider's website or related documentation. Provides an HTTPS link to the provider's official website, product page, or related documentation for users to learn more or obtain support. |

## AgentCapabilities

Defines the optional capabilities supported by an agent.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| streaming     | boolean  | No   | Yes   | Whether the agent supports streaming responses.<br>true: indicates support for SSE (Server-Sent Events) streaming responses, returning partial results in real time.<br>false: indicates no support for streaming, and only a complete result is returned at once. After streaming responses are enabled, the client can use the stream method to obtain the real-time data stream. |
| pushNotifications     | boolean  | No   | Yes   | Whether the agent supports sending push notifications for asynchronous task updates.<br>true: indicates support. When the state of a long-running task changes (for example, task completion, failure, or progress update), the agent can proactively push notifications to the client.<br>false: indicates no support, and the client needs to poll to query the task state. |
| stateTransitionHistory | boolean | No | Yes | Whether the agent supports viewing the task state transition history.<br>true: indicates support. The client can query the complete state transition records of a task from creation to completion (for example, pending->running->completed).<br>false: indicates no support for state history query. |
| extendedAgentCard     | boolean  | No   | Yes   | Whether the agent supports providing an extended AgentCard during authentication.<br>true: indicates support. After passing authentication, the client can obtain an extended AgentCard that contains additional information (such as private configuration and advanced capabilities).<br>false: only a basic AgentCard is provided. The default value is false when this parameter is not passed in. |
| extension     | string  | No   | Yes   | Protocol extension supported by the agent. It is used to store custom extension capability configurations in JSON string format, and can contain protocol-level extension parameters and custom fields agreed upon by the developer and the agent consumer. The extension configuration is not used when this parameter is not configured. |

## AgentSkill

Represents the different capabilities or functions that an agent can perform.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| id     | string  | No   | No   | Unique identifier of the AgentSkill, which must be unique within an AgentCard. It is recommended to use a semantic naming format (for example, "route-planner" or "recipe-search") to precisely specify the skill to use in API calls. |
| name     | string  | No   | No   | Name of the AgentSkill. It is used for display in the UI, for example, "Route Planning" or "Recipe Search". |
| description     | string  | No   | No   | Detailed description of the AgentSkill. It should clearly describe the specific functions, applicable scenarios, and problems that the skill can solve, for example, "Helps users plan a travel route between two points, providing multiple transportation options and real-time traffic information". |
| tags     | Array\<string>  | No   | No   | Keyword tags that describe the capabilities of the AgentSkill. They are used for skill classification, retrieval, and recommendation, for example, ["maps", "routing", "navigation"] or ["cooking", "recipe", "food"]. Tags should be concise and clear for easy understanding and searching by users. |
| examples     | Array\<string>  | No   | Yes   | Example prompts or usage scenarios that the AgentSkill can handle. Providing specific examples helps users understand how to use the skill, for example, ["Plan a route from Shanghai to Beijing"]. If not configured, no examples are displayed. |
| inputModes     | Array\<string>  | No   | Yes   | Input modes supported by the AgentSkill. They are defined in MIME type format, for example, ["text/plain"]. If not set, defaultInputModes at the AgentCard level is used. This field allows customizing the input type for a specific skill, overriding the default setting. |
| outputModes     | Array\<string>  | No   | Yes   | Output modes supported by the AgentSkill. They are defined in MIME type format, for example, ["text/plain", "application/html", "video/mp4"]. If not set, defaultOutputModes at the AgentCard level is used. This field allows customizing the output type for a specific skill, overriding the default setting. |
| extension     | string  | No   | Yes   | Extension configuration item of the AgentSkill. It is used to store skill-level custom extension configurations in JSON string format, and can contain skill-specific parameters and configuration information. If not configured, no extension configuration is used.|

## AgentAppInfo

App information of the Agent.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

| Name               | Type    | Read-only | Optional | Description                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| bundleName     | string  | No   | No   | Bundle name of the AgentExtensionAbility to which the Agent belongs. |
| moduleName     | string  | No   | No   | Module name of the AgentExtensionAbility to which the Agent belongs. |
| abilityName     | string  | No   | No   | Ability name of the AgentExtensionAbility to which the Agent belongs. |
| deviceTypes     | Array\<string>  | No   | Yes   | List of device types supported by the Agent. For the value range, see [deviceTypes](../../quick-start/module-configuration-file.md#devicetypes). |
| minAppVersion     | string  | No   | Yes   | Minimum application version required for the Agent to run. Uses the semantic versioning format (for example, "1.0.0") to specify the minimum application version required to run the Agent. Applications with a version lower than this value cannot correctly load and run the Agent. |
