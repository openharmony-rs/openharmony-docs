# AgentExtensionAbility Configuration File Description

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1630992de2f5af1dcca3ca27d11e23e0321182c9 translatedAt=2026-05-30T07:46:28.153Z pushedAt=2026-06-01T09:24:00.708Z -->

[AgentCard](../reference/apis-ability-kit/js-apis-inner-application-AgentCard.md) serves as the "business card" of an Agent, primarily used to describe the Agent's capabilities. The detailed configuration information of an AgentCard needs to be carried through the agent_config.json configuration file.

This configuration file is manually created by the developer and is usually located in the Module's `resources/base/profile/` directory. AgentExtensionAbility can reference this resource file in the metadata configuration item to bind the corresponding AgentCard. One agent_config.json can only be referenced by one AgentExtensionAbility.

## agent_config.json Configuration File Field Description

| Tag | Description | Data Type | Mandatory |
| -------- | -------- | -------- | -------- |
| [agentCards](#agentcards-tag) | The list of AgentCard configuration information contained in AgentExtensionAbility. | Object array | Yes |

## agentCards Tag

This tag describes the internal structure of the AgentCard object.

| Attribute Name | Description | Data Type | Mandatory |
| -------- | -------- | -------- | -------- |
| agentId | Unique identifier of the Agent. The agentId must be unique within the same application. The maximum length is 64 bytes. | string | Yes |
| name | Name of the Agent, generally used by the consumer to display in the UI, for example, "Recipe Assistant". The maximum length is 64 bytes. | string | Yes |
| description | Description of the Agent's functionality. This description should clearly explain the Agent's core functions and purposes, helping users understand what the Agent can do, for example, "Helps users search for recipes, plan menus, and provide cooking suggestions". The maximum length is 512 bytes. | string | Yes |
| [provider](#provider-tag) | Service provider information of the Agent, including the provider's organization name and official website URL, used to identify the source and copyright information of the Agent. | object | Optional. The default value is empty. |
| version | Version number of the Agent, following the Semantic Versioning specification (e.g., "1.0.0"). The format is defined by the provider. The version number is used to identify functional iterations and compatibility changes of the Agent. The maximum length is 32 bytes. | string | Yes |
| documentationUrl | URL of the Agent's documentation, providing detailed usage guides, API descriptions, examples, and best practice guides to help developers better integrate and use the Agent. The maximum length is 512 bytes. | string | Optional. The default value is empty. |
| [capabilities](#capabilities-tag) | Set of optional capabilities supported by the Agent, defining other optional capabilities supported by the Agent, such as streaming responses, push notifications, and state history queries. | object | Optional. The default value is empty. |
| defaultInputModes | Set of input modes supported by the Agent across all [skills](#skills-tag), using MIME type format to define supported input media types, for example, ["text/plain"] indicates plain text input, ["application/json"] indicates JSON structured data input, ["image/png"] indicates image input. The inputModes at the [skill](#skills-tag) level will override this default setting. The maximum length of each element in the array is 32 bytes. | string array | Yes |
| defaultOutputModes | Set of output modes supported by the Agent across all [skills](#skills-tag), using MIME type format to define supported output media types, for example, ["text/plain"] indicates plain text output, ["application/html"] indicates HTML format output, ["application/json"] indicates JSON data output. The outputModes at the [skill](#skills-tag) level will override this default setting. The maximum length of each element in the array is 32 bytes. | string array | Yes |
| [skills](#skills-tag) | Collection of functionalities provided by the Agent, describing the specific functions or skills that the Agent can perform. Each skill defines its specific purpose, tags, and usage examples. The Agent must contain at least one skill. | object array | Yes |
| iconUrl | URL of the Agent's icon, providing a visual identifier icon for the Agent, used for display in the UI to enhance the Agent's recognizability and user experience. The maximum length is 512 bytes. | string | Yes |
| category | Category of the Agent, used for classifying and managing Agents. Common categories include: "productivity", "entertainment", "education", "finance", "health", etc. The maximum length is 64 bytes. | string | Yes |
| extension | Extension configuration item of the Agent, used to store custom extension configuration information, such as the Agent's opening remarks and version protocol number. The format is a JSON string. The maximum length is 5120 bytes. | string | Optional. The default value is empty. |
| [appInfo](#appinfo-tag) | Application information where the Agent resides, including the Agent's device type and the minimum runnable version number, used to locate and manage the AgentExtensionAbility instance. | object | Optional. For the default value, see [appInfo](#appinfo-tag). |

### provider Tag

This tag describes the internal structure of the provider object.

| Attribute Name | Description | Data Type | Mandatory |
| -------- | -------- | -------- | -------- |
| organization | The organization name of the Agent provider, identifying the company, organization, or individual that develops or provides the Agent. The maximum length is 128 bytes. | string | Yes |
| url | The URL of the Agent provider's website or related documentation. Provides an HTTPS link to the provider's official website, product page, or related documentation for users to learn more or get support. The maximum length is 512 bytes. | string | Yes |

### capabilities Tag

This tag describes the internal structure of the capabilities object.

| Attribute Name | Description | Data Type | Mandatory |
| -------- | -------- | -------- | -------- |
| streaming | Whether the Agent supports streaming responses.<br>true: Indicates support for SSE (Server-Sent Events) streaming responses, allowing partial results to be returned in real time.<br>false: Indicates streaming is not supported; only a one-time complete result is returned. | boolean | Optional, default value is false. |
| pushNotifications | Whether the Agent supports sending push notifications for asynchronous task updates.<br>true: Indicates support. When the status of a long-running task changes (such as task completion, failure, or progress update), the Agent can actively push notifications to the client.<br>false: Indicates no support; the client needs to poll to query the task status. | boolean | Optional, default value is false. |
| stateTransitionHistory | Whether the Agent supports viewing the history of task state changes.<br>true: Indicates support. The client can query the complete state transition record of a task from creation to completion (e.g., pending->running->completed).<br>false: Indicates state history query is not supported. | boolean | Optional, default value is false. |
| extendedAgentCard | Whether the Agent supports providing an extended AgentCard during authentication.<br>true: Indicates support. After authentication, the client can obtain an extended AgentCard containing additional information (such as private configurations and advanced capabilities).<br>false: Indicates only the basic AgentCard is provided. | boolean | Optional, default value is false. |
| extension | Protocol extensions supported by the Agent, used to store custom extension capability configurations. The format is a JSON string, which can contain protocol-level extension parameters and custom fields, as agreed upon by the developer and the Agent user. The maximum length is 2048 bytes. | string | Optional, default value is empty. |

### skills tag

This tag describes the internal structure of the skill object.

| Attribute Name | Description | Data Type | Mandatory |
| -------- | -------- | -------- | -------- |
| id | Unique identifier of the skill, which must be unique within an AgentCard. It is recommended to use a semantic naming format (such as "route-planner" or "recipe-search") to precisely specify the skill to be used in API calls. The maximum length is 64 bytes. | string | Yes |
| name | Name of the skill, displayed in the UI, for example, "Route Planning" or "Recipe Search". The maximum length is 128 bytes. | string | Yes |
| description | Detailed description of the skill, which should clearly explain the specific functions, applicable scenarios, and problems it can solve, for example, "Helps users plan travel routes between two points, offering multiple transportation options and real-time traffic information". The maximum length is 512 bytes. | string | Yes |
| tags | Keyword tags describing the skill's capabilities, used for skill classification, retrieval, and recommendation, for example, ["maps", "routing", "navigation"] or ["cooking", "recipe", "food"]. Tags should be concise and clear for easy user understanding and searching. The maximum length of a single element is 32 bytes. | string array | Yes |
| examples | Example prompts or usage scenarios that the skill can handle. Providing specific examples helps users understand how to use the skill, for example, ["Plan a route from Shanghai to Beijing"]. The maximum length of a single element is 256 bytes. | string array | Optional. The default value is empty. |
| inputModes | Input modes supported by the skill, defined using MIME type format, for example, ["text/plain"]. If not set, the AgentCard-level defaultInputModes will be used. This field allows customizing input types for a specific skill, overriding the default settings. The maximum length of each element in the array is 32 bytes. | string array | Optional. The default value is empty. |
| outputModes | Output modes supported by the skill, defined using MIME type format, for example, ["text/plain", "application/html", "video/mp4"]. If not set, the AgentCard-level defaultOutputModes will be used. This field allows customizing output types for a specific skill, overriding the default settings. The maximum length of each element in the array is 32 bytes. | string array | Optional. The default value is empty. |
| extension | Extension configuration item for the skill, used to store custom extension configurations. The format is a JSON string, which can contain skill-specific parameters and configuration information. The maximum length is 1024 bytes. | string | Optional. The default value is empty. |

### appInfo Tag

This tag describes the internal structure of the appInfo object.

| Attribute Name | Description | Data Type | Mandatory |
| -------- | -------- | -------- | -------- |
| deviceTypes | List of device types supported by the Agent. For the value range, see [deviceTypes](../quick-start/module-configuration-file.md#devicetypes). The device type list configured for the Agent must be a subset of the device type list of the owning Module. If device types outside the Module are configured, the system will ignore them. | string array | Optional. The default value is the application's deviceTypes. |
| minAppVersion | Minimum application version required for the Agent to run, using the semantic versioning format (e.g., "1.0.0"). Specifies the minimum application version required to run this Agent. Applications with a version lower than this will not be able to load and run the Agent correctly. The maximum length is 32 bytes. | string | Optional. The default value is empty. |

## Example of the agent_config.json Configuration File

```json
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
          "description": "Query real-time weather information for a specified city",
          "tags": ["Weather", "Query", "Real-time"],
          "examples": [
            "What's the weather like in Beijing today",
            "Check the current weather in Shanghai",
            "Check the weather in Shenzhen today"
          ],
          "inputModes": ["text/plain"],
          "outputModes": ["text/plain", "application/json"],
          "extension": ""
        },
        {
          "id": "weather_forecast",
          "name": "Weather Forecast",
          "description": "Get the weather forecast for a specified city for the next few days",
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
      "extension": "",
      "appInfo": {
        "deviceTypes": ["phone", "tablet"],
        "minAppVersion": "1.0.0"
      }
    }
  ]
}
```