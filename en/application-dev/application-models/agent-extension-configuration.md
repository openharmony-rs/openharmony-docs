# AgentExtensionAbility Configuration File Description
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a7527b1bdb02bfea835e9bc50c20bb3d2f59d798 translatedAt=2026-11-02T13:37:24.854Z pushedAt=2026-11-03T06:53:00.482Z nl=1 -->

[AgentCard](../reference/apis-ability-kit/js-apis-inner-application-AgentCard.md) serves as the "business card" of an Agent and is mainly used to describe the Agent's capabilities. The detailed configuration of an AgentCard is carried by the agent_config.json configuration file.

This configuration file is manually created by developers and is usually located in the `resources/base/profile/` directory of a Module. AgentExtensionAbility can reference this resource file in the metadata configuration item to bind the corresponding AgentCard. An agent_config.json file can be referenced by only one AgentExtensionAbility.

## Fields in the agent_config.json Configuration File

| Tag | Description | Data Type | Optional |
| -------- | -------- | -------- | -------- |
| [agentCards](#agentcards) | List of AgentCard configuration information contained in AgentExtensionAbility. | Object array | No |

## agentCards

This tag describes the internal structure of an AgentCard object.

| Name | Description | Data Type | Optional |
| -------- | -------- | -------- | -------- |
| agentId | Unique identifier of the Agent. It must be unique within the same application. The maximum length is 64 bytes. | String | No |
| name | Name of the Agent, generally used by the caller to display to users in the UI, for example, "Recipe Assistant". The maximum length is 64 bytes. | String | No |
| description | Description of the Agent's functions. The description should clearly explain the core functions and purpose of the Agent to help users understand what the Agent can do, for example, "Helps users search for recipes, plan menus, and provide cooking suggestions". The maximum length is 512 bytes. | String | No |
| [provider](#provider-tag) | Service provider information of the Agent, including the provider's organization name and official website URL, used to identify the source and copyright information of the Agent. | Object | Optional. The default is empty. |
| version | Version number of the Agent, following the semantic versioning specification (for example, "1.0.0"). The format is defined by the provider. The version number is used to identify the functional iteration and compatibility changes of the Agent. The maximum length is 32 bytes. | String | No |
| documentationUrl | URL of the Agent documentation, providing detailed Agent usage documentation, API descriptions, examples, and best practice guides to help developers better integrate and use the Agent. The maximum length is 512 bytes. | String | Optional. The default is empty. |
| [capabilities](#capabilities-tag) | Set of optional capabilities supported by the Agent, defining other optional capabilities supported by the Agent, such as streaming responses, push notifications, and state history queries. | Object | Optional. The default is empty. |
| defaultInputModes | Set of input modes supported by the Agent across all [skills](#skills-tag), using the MIME type format to define the supported input media types, for example, ["text/plain"] for plain text input, ["application/json"] for JSON structured data input, and ["image/png"] for image input. The inputModes at the [skill](#skills-tag) level override this default setting. The maximum length of each element in the array is 32 bytes. | String array | No |
| defaultOutputModes | Set of output modes supported by the Agent across all [skills](#skills-tag), using the MIME type format to define the supported output media types, for example, ["text/plain"] for plain text output, ["application/html"] for HTML format output, and ["application/json"] for JSON data output. The outputModes at the [skill](#skills-tag) level override this default setting. The maximum length of each element in the array is 32 bytes. | String array | No |
| [skills](#skills-tag) | Set of functions provided by the Agent, describing the specific functions or skills that the Agent can perform. Each skill defines its specific purpose, tags, and usage examples. The Agent must contain at least one skill. | Object array | No |
| iconUrl | URL of the Agent icon, providing a visual identification icon for the Agent, used for display in the UI to enhance the recognizability and user experience of the Agent. The maximum length is 512 bytes.<br>**Note:** The system does not verify the content of this field. The caller must verify the validity and security of iconUrl. | String | No |
| category | Category of the Agent, used for classifying and managing Agents. Common categories include "productivity", "entertainment", "education", "finance", and "health". The maximum length is 64 bytes. | String | No |
| type | Type of the Agent card. Supports numeric enumeration and string enumeration names:<br>- 0: application type, which can also use APP as the value.<br>- 1: atomic service type, which can also use ATOMIC_SERVICE as the value.<!--Del--><br>- 2: low-code type, which can also use LOW_CODE as the value. This field applies only to system applications.<!--DelEnd--> <br>If not specified, the default is the APP type.<br>**Note:** Supported since API version 26.0.0. | Integer or string | Optional. The default is 0 (APP). |
| extension | Extended configuration item of the Agent, used to store custom extended configuration information, such as the Agent's opening remarks and version protocol number. The format is a JSON string. The maximum length is 5120 bytes. | String | No |
| [appInfo](#appinfo-tag) | Application information of the Agent, including the Agent device types and the minimum runnable version number, used to locate and manage AgentExtensionAbility instances. | Object | Optional. For the default value, see [appInfo](#appinfo-tag). |

### provider Tag

This tag describes the internal structure of the provider object.

| Name | Description | Data Type | Optional |
| -------- | -------- | -------- | -------- |
| organization | Organization name of the Agent provider, identifying the company, organization, or individual that develops or provides the Agent. The maximum length is 128 bytes. | String | No |
| url | URL of the Agent provider's website or related documentation, providing an HTTPS link to the provider's official website, product page, or related documentation for users to learn more or obtain support. The maximum length is 512 bytes. | String | No |

### capabilities Tag

This tag describes the internal structure of the capabilities object.

| Name | Description | Data Type | Optional |
| -------- | -------- | -------- | -------- |
| streaming | Whether the Agent supports streaming responses.<br>true: indicates support for SSE (Server-Sent Events) streaming responses, which can return partial results in real time.<br>false: indicates that streaming is not supported and only a one-time complete result is returned. | Boolean value | Optional. The default is false. |
| pushNotifications | Whether the agent supports sending push notifications for asynchronous task updates.<br>true: indicates support. When the state of a long-running task changes (for example, task completion, failure, or progress update), the agent can proactively push notifications to the client.<br>false: indicates no support, and the client needs to poll to query the task state. | Boolean value | Optional. The default is false. |
| stateTransitionHistory | Whether the agent supports viewing the task state transition history.<br>true: indicates support. The client can query the complete state transition records of a task from creation to completion (for example, pending->running->completed).<br>false: indicates no support for state history query. | Boolean value | Optional. The default is false. |
| extendedAgentCard | Whether the Agent supports providing an extended AgentCard during authentication.<br>true: indicates support. After passing authentication, the client can obtain an extended AgentCard that contains additional information (such as private configuration and advanced capabilities).<br>false: only a basic AgentCard is provided. | Boolean value | Optional. The default is false. |
| extension | Protocol extension supported by the Agent, used to store custom extended capability configuration. The format is a JSON string, which can contain protocol-level extension parameters and custom fields agreed upon by the developer and the Agent caller. The maximum length is 2048 bytes. | String | No |

### skills Tag

This tag describes the internal structure of a skill object.

| Name | Description | Data Type | Optional |
| -------- | -------- | -------- | -------- |
| id | Unique identifier of the skill. It must be unique within an AgentCard. It is recommended to use a semantic naming format (for example, "route-planner" or "recipe-search") to precisely specify the skill to use in API calls. The maximum length is 64 bytes. | String | No |
| name | Name of the skill, used for display in the UI, for example, "Route Planning" or "Recipe Search". The maximum length is 128 bytes. | String | No |
| description | Detailed description of the skill. It should clearly explain the specific functions, applicable scenarios, and problems that the skill can solve, for example, "Helps users plan travel routes between two points, providing multiple transportation options and real-time traffic information". The maximum length is 512 bytes. | String | No |
| tags | Keyword tags that describe the skill capabilities, used for skill classification, retrieval, and recommendation, for example, ["maps", "routing", "navigation"] or ["cooking", "recipe", "food"]. Tags should be concise and clear for easy understanding and searching. The maximum length of a single element is 32 bytes. | String array | No |
| examples | Example prompts or usage scenarios that the skill can handle. Providing specific examples helps users understand how to use the skill, for example, ["Plan a route from Shanghai to Beijing"]. The maximum length of a single element is 256 bytes. | String array | Optional. The default is empty. |
| inputModes | Input modes supported by the skill, defined using the MIME type format, for example, ["text/plain"]. If not set, the AgentCard-level defaultInputModes is used. This field allows customizing the input type for a specific skill, overriding the default setting. The maximum length of each element in the array is 32 bytes. | String array | Optional. The default is empty. |
| outputModes | Output modes supported by the skill, defined using the MIME type format, for example, ["text/plain", "application/html", "video/mp4"]. If not set, the AgentCard-level defaultOutputModes is used. This field allows customizing the output type for a specific skill, overriding the default setting. The maximum length of each element in the array is 32 bytes. | String array | Optional. The default is empty. |
| extension | Extended configuration item of the skill, used to store custom extended configuration. The format is a JSON string, which can contain skill-specific parameters and configuration information. The maximum length is 1024 bytes. | String | No |

### appInfo Tag

This tag describes the internal structure of the appInfo object.

| Name | Description | Data Type | Optional |
| -------- | -------- | -------- | -------- |
| deviceTypes | List of device types supported by the Agent. For the value range, see [deviceTypes](../quick-start/module-configuration-file.md#devicetypes). The device type list configured for the Agent must be a subset of the device type list of the Module to which it belongs. If device types outside the Module are configured, the system ignores them. | String array | Optional. The default is the deviceTypes of the application. |
| minAppVersion | Minimum application version required for the Agent to run. Uses the semantic versioning format (for example, "1.0.0") to specify the minimum application version required to run the Agent. Applications with a version lower than this value cannot correctly load and run the Agent. The maximum length is 32 bytes. | String | Optional. The default is empty. |

## Example of the agent_config.json Configuration File

```json5
{
  "agentCards": [
    {
      "agentId": "weather_assistant_001",
      "name": "WeatherAssistant",
      "description": "An intelligent assistant that provides weather query and weather forecast services",
      "provider": {
        "organization": "Example Weather Inc.",
        "url": "https://example.com"
      },
      "version": "1.0.0",
      "documentationUrl": "https://example.com/docs/weather-agent",
      "capabilities": {
        "streaming": true,
        "pushNotifications": true,
        "stateTransitionHistory": true,
        "extendedAgentCard": false,
        "extension": "custom_protocol_v1"
      },
      "defaultInputModes": ["text/plain", "audio/wav"],
      "defaultOutputModes": ["text/plain", "application/json"],
      "skills": [
        {
          "id": "get_weather",
          "name": "Get Weather",
          "description": "Query the real-time weather information of a specified city",
          "tags": ["Weather", "Query", "Real-time"],
          "examples": [
            "What is the weather like in Beijing today",
            "Query the current weather in Shanghai",
            "Check the weather in Shenzhen today for me"
          ],
          "inputModes": ["text/plain"],
          "outputModes": ["text/plain", "application/json"],
          "extension": "custom_protocol_v1"
        },
        {
          "id": "weather_forecast",
          "name": "Weather Forecast",
          "description": "Obtain the weather forecast for a specified city for the next few days",
          "tags": ["Weather", "Forecast", "Future"],
          "examples": [
            "I need the weather forecast for Guangzhou for the next three days",
            "Tell me the weather in Hangzhou tomorrow"
          ],
          "inputModes": ["text/plain"],
          "outputModes": ["text/plain", "application/json"]
        }
      ],
      "iconUrl": "common/weather_icon.png",
      "category": "Life Services",
      "type": "APP", // string enum type
      // "type": "0", // numeric enum type
      "extension": "custom_protocol_v1",
      "appInfo": {
        "deviceTypes": ["phone", "tablet"],
        "minAppVersion": "1.0.0"
      }
    }
  ]
}
```
