# @ohos.app.ability.common (Ability Common Module) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=938bc44e514b9eed279585f3283eccb3aaf0ac72 translatedAt=2026-09-03T10:08:40.899Z pushedAt=2026-09-08T07:19:00.017Z -->

You can use this module to reference the ability public module class.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.app.ability.common (Ability Common Module)](js-apis-app-ability-common.md).

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## ServiceExtensionContext

type ServiceExtensionContext = _ServiceExtensionContext.default

Level-2 module ServiceExtensionContext.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [ServiceExtensionContext](js-apis-inner-application-serviceExtensionContext-sys.md) | Second-level module of ServiceExtensionContext. |

## AutoFillExtensionContext<sup>11+</sup>

type AutoFillExtensionContext = _AutoFillExtensionContext.default

Level-2 module AutoFillExtensionContext.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [AutoFillExtensionContext](js-apis-inner-application-autoFillExtensionContext-sys.md) | Second-level module of AutoFillExtensionContext. |

## AutoStartupInfo<sup>11+</sup>

type AutoStartupInfo = _AutoStartupInfo

Level-2 module AutoStartupInfo.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AutoStartupInfo](js-apis-inner-application-autoStartupInfo-sys.md) | Level-2 module AutoStartupInfo.|

## AutoStartupCallback<sup>11+</sup>

type AutoStartupCallback = _AutoStartupCallback

Level-2 module AutoStartupCallback.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AutoStartupCallback](js-apis-inner-application-autoStartupCallback-sys.md) | Level-2 module AutoStartupCallback.|

## UIServiceExtensionContext<sup>14+</sup>

type UIServiceExtensionContext = _UIServiceExtensionContext.default

Level-2 module UIServiceExtensionContext.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [UIServiceExtensionContext](js-apis-inner-application-uiserviceExtensionContext-sys.md) | Second-level module of UIServiceExtensionContext. |

## UIServiceHostProxy<sup>14+</sup>

type UIServiceHostProxy = _UIServiceHostProxy.default

Level-2 module UIServiceHostProxy.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [UIServiceHostProxy](js-apis-inner-application-uiservicehostproxy-sys.md) | Second-level module of UIServiceHostProxy. |

## AgentProxy<sup>24+</sup>

type AgentProxy = _AgentProxy

Second-level module of AgentProxy.

[AgentProxy](../apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) is used to send data or security authentication requests from the client to the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentProxy](../apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) | Used to send data or security authentication requests from the client to the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server. |

## AgentExtensionConnectCallback<sup>24+</sup>

type AgentExtensionConnectCallback = _AgentExtensionConnectCallback

Second-level module of AgentExtensionConnectCallback.

[AgentExtensionConnectCallback](../apis-ability-kit/js-apis-inner-application-agentExtensionConnectCallback-sys.md) provides callback APIs for developers to receive data and security authentication requests sent by the server, and to detect the disconnection of the AgentExtensionAbility server.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_AgentExtensionConnectCallback](../apis-ability-kit/js-apis-inner-application-agentExtensionConnectCallback-sys.md) | Provides callback APIs for developers to receive data and security authentication requests sent by the server, and to detect the disconnection of the AgentExtensionAbility server. |

## ToolInfo

type ToolInfo = _ToolInfo

[ToolInfo](../apis-ability-kit/js-apis-inner-application-ToolInfo-sys.md#toolinfo) describes the basic information about a system command-line tool (CLI).

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_ToolInfo](../apis-ability-kit/js-apis-inner-application-ToolInfo-sys.md#toolinfo) | Describes the basic information about a system command-line tool (CLI). |

## ToolSummary

type ToolSummary = _ToolSummary

[ToolSummary](../apis-ability-kit/js-apis-inner-application-ToolInfo-sys.md#toolsummary) describes the summary information of a system command-line tool (CLI).

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_ToolSummary](../apis-ability-kit/js-apis-inner-application-ToolInfo-sys.md#toolsummary) | Describes the summary information of a system command-line tool (CLI). |

## CliToolEvent

type CliToolEvent = _CliToolEvent

[CliToolEvent](../apis-ability-kit/js-apis-inner-application-cliToolEvent-sys.md) describes the session event information generated during the runtime of the CLI tool process.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_CliToolEvent](../apis-ability-kit/js-apis-inner-application-cliToolEvent-sys.md) | Describes the session event information generated during the runtime of the CLI tool process. |

## ToolEventCallback

type ToolEventCallback = _ToolEventCallback

[ToolEventCallback](../apis-ability-kit/js-apis-inner-application-toolEventCallback-sys.md) is used to receive session events generated by the CLI tool process during runtime.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_ToolEventCallback](../apis-ability-kit/js-apis-inner-application-toolEventCallback-sys.md) | Used to receive session events generated by the CLI tool process during runtime. |

## FunctionInfo

type FunctionInfo = _FunctionInfo

[FunctionInfo](../apis-ability-kit/js-apis-inner-application-FunctionInfo-sys.md#functioninfo) describes the basic information of a [Function](./js-apis-app-function-functionManager-sys.md).

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

| Type | Description |
| --- | --- |
| [_FunctionInfo](../apis-ability-kit/js-apis-inner-application-FunctionInfo-sys.md#functioninfo) | Describes the basic information of a Function, including the Function namespace, name, version, description, input and output modes, and so on. |

**Example**

```ts
import { common } from '@kit.AbilityKit';

let uiAbilityContext: common.UIAbilityContext;
let abilityStageContext: common.AbilityStageContext;
let applicationContext: common.ApplicationContext;
let baseContext: common.BaseContext;
let context: common.Context;
let extensionContext: common.ExtensionContext;
let formExtensionContext: common.FormExtensionContext;
let vpnExtensionContext: common.VpnExtensionContext;
let eventHub: common.EventHub;
let pacMap: common.PacMap;
let abilityResult: common.AbilityResult;
let abilityStartCallback: common.AbilityStartCallback;
let connectOptions: common.ConnectOptions;
let autoFillExtensionContext: common.AutoFillExtensionContext;
let uiServiceExtensionContext: common.UIServiceExtensionContext;
let uiServiceHostProxy: common.UIServiceHostProxy;
let agentProxy: common.AgentProxy;
let agentExtensionConnectCallback: common.AgentExtensionConnectCallback;
let toolInfo: common.ToolInfo;
let toolSummary: common.ToolSummary;
let cliToolEvent: common.CliToolEvent;
let toolEventCallback: common.ToolEventCallback;
let functionInfo: common.FunctionInfo;
```
