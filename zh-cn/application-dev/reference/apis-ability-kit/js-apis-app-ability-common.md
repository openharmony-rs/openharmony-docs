# @ohos.app.ability.common (Ability公共模块)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块提供Ability Kit中常用公共能力的纯类型定义，包含各类上下文对象、回调接口和数据结构。本模块仅导出类型声明，不包含具体实现逻辑或可执行代码。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## UIAbilityContext

type UIAbilityContext = _UIAbilityContext.default

[UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)组件上下文，继承自Context。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_UIAbilityContext.default](js-apis-inner-application-uiAbilityContext.md) | UIAbilityContext组件上下文。 |

## AbilityStageContext

type AbilityStageContext = _AbilityStageContext.default

[AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md)组件上下文，继承自Context。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AbilityStageContext.default](js-apis-inner-application-abilityStageContext.md) | AbilityStage组件上下文。 |

## ApplicationContext

type ApplicationContext = _ApplicationContext.default

应用上下文，继承自Context。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_ApplicationContext.default](js-apis-inner-application-applicationContext.md) | 应用上下文。 |

## BaseContext

type BaseContext = _BaseContext.default

所有Context类型的父类。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_BaseContext.default](js-apis-inner-application-baseContext.md) | 所有Context的父类。 |

## Context

type Context = _Context.default

[Stage模型](../../application-models/ability-terminology.md#stage模型)的上下文基类。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_Context.default](js-apis-inner-application-context.md) | Stage模型的上下文基类。 |

## ExtensionContext

type ExtensionContext = _ExtensionContext.default

[ExtensionAbility](../apis-ability-kit/js-apis-app-ability-extensionAbility.md)组件上下文，继承自Context。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_ExtensionContext.default](js-apis-inner-application-extensionContext.md) | ExtensionAbility组件上下文。 |

## FormExtensionContext

type FormExtensionContext = _FormExtensionContext.default

[FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md)组件上下文，继承自[ExtensionContext](./js-apis-inner-application-extensionContext.md)。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_FormExtensionContext.default](../apis-form-kit/js-apis-inner-application-formExtensionContext.md) | FormExtensionAbility组件上下文。 |

## VpnExtensionContext<sup>11+<sup>

type VpnExtensionContext = _VpnExtensionContext.default

[VpnExtensionAbility](../apis-network-kit/js-apis-VpnExtensionAbility.md)组件上下文，继承自Context。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_VpnExtensionContext.default](../apis-network-kit/js-apis-inner-application-VpnExtensionContext.md) | VpnExtensionAbility组件上下文。 |

## EventHub

type EventHub = _EventHub.default

EventHub是系统提供的基于发布-订阅模式实现的事件通信机制。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_EventHub.default](js-apis-inner-application-eventHub.md) | 系统提供的基于发布-订阅模式实现的事件通信机制。 |

## PacMap

type PacMap = _PacMap

存储基础数据类型的容器。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 类型 | 说明 |
| --- | --- |
| [_PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap) | 存储基础数据类型的容器。 |

## AbilityResult

type AbilityResult = _AbilityResult

定义Ability被拉起并退出后返回的结果码和数据。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AbilityResult](js-apis-inner-ability-abilityResult.md) | 定义Ability被拉起并退出后返回的结果码和数据。 |

## AbilityStartCallback<sup>11+<sup>

type AbilityStartCallback = _AbilityStartCallback

定义了拉起UIExtensionAbility的回调结果，通常作为[UIAbilityContext.startAbilityByType](js-apis-inner-application-uiAbilityContext.md#startabilitybytype11)/[UIExtensionContext.startAbilityByType](js-apis-app-ability-uiExtensionContentSession.md#startabilitybytype11)的入参传入。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AbilityStartCallback](js-apis-inner-application-abilityStartCallback.md) | 定义拉起UIExtensionAbility的回调结果。 |

## ConnectOptions

type ConnectOptions = _ConnectOptions

在连接指定的后台服务时作为入参，用于接收与后台服务的连接状态。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_ConnectOptions](js-apis-inner-ability-connectOptions.md) | 在连接指定的后台服务时作为入参，用于接收与后台服务的连接状态。 |

## UIExtensionContext<sup>10+</sup>

type UIExtensionContext = _UIExtensionContext.default

[UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)组件上下文，继承自Context。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_UIExtensionContext.default](js-apis-inner-application-uiExtensionContext.md) | UIExtensionAbility组件上下文。 |

## EmbeddableUIAbilityContext<sup>12+<sup>

type EmbeddableUIAbilityContext = _EmbeddableUIAbilityContext.default

[EmbeddableUIAbility](../apis-ability-kit/js-apis-app-ability-embeddableUIAbility.md)组件上下文，继承自Context。

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_EmbeddableUIAbilityContext.default](js-apis-inner-application-EmbeddableUIAbilityContext.md) | EmbeddableUIAbility组件上下文。 |

## PhotoEditorExtensionContext<sup>12+<sup>

type PhotoEditorExtensionContext = _PhotoEditorExtensionContext.default

[PhotoEditorExtensionAbility](../apis-ability-kit/js-apis-app-ability-photoEditorExtensionAbility.md)组件上下文，继承自Context。

**系统能力**：SystemCapability.Ability.AppExtension.PhotoEditorExtension

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_PhotoEditorExtensionContext.default](js-apis-app-ability-photoEditorExtensionContext.md) | PhotoEditorExtensionAbility组件上下文。 |

## UIServiceProxy<sup>14+<sup>

type UIServiceProxy = _UIServiceProxy.default

UIServiceProxy提供了与UIServiceExtensionAbility服务端数据通信的能力。UIServiceExtensionAbility是一类特殊的ExtensionAbility组件，这类组件由系统提供，通常用于提供浮窗组件相关扩展能力。

**原子化服务API**：从API version 14开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_UIServiceProxy.default](js-apis-inner-application-uiserviceproxy.md) | 提供与UIServiceExtensionAbility服务端数据通信的能力。 |

## UIServiceExtensionConnectCallback<sup>14+<sup>

type UIServiceExtensionConnectCallback = _UIServiceExtensionConnectCallback.default

在连接指定的UIServiceExtensionAbility服务时作为入参，用于提供UIServiceExtensionAbility连接回调数据能力。

**原子化服务API**：从API version 14开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_UIServiceExtensionConnectCallback.default](js-apis-inner-application-uiServiceExtensionconnectcallback.md) | 提供UIServiceExtensionAbility连接回调数据能力。 |

## AppServiceExtensionContext<sup>20+</sup>

type AppServiceExtensionContext = _AppServiceExtensionContext.default

[AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md)组件上下文，继承自Context。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AppServiceExtensionContext.default](js-apis-inner-application-appServiceExtensionContext.md) | AppServiceExtensionAbility组件上下文。 |

## FormEditExtensionContext<sup>22+</sup>

type FormEditExtensionContext = _FormEditExtensionContext.default

[FormEditExtensionAbility](../apis-form-kit/js-apis-app-form-formEditExtensionAbility.md)组件上下文，继承自[UIExtensionContext](./js-apis-inner-application-uiExtensionContext.md)。

**原子化服务API**：从API version 22开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.Form

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_FormEditExtensionContext.default](../apis-form-kit/js-apis-inner-application-formEditExtensionContext.md) | FormEditExtensionAbility组件上下文。 |

## LiveFormExtensionContext<sup>22+</sup>

type LiveFormExtensionContext = _LiveFormExtensionContext.default

[LiveFormExtensionAbility](../apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md)组件上下文，继承自[ExtensionContext](./js-apis-inner-application-extensionContext.md)。

**原子化服务API**：从API version 22开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.Form

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_LiveFormExtensionContext.default](../apis-form-kit/js-apis-application-LiveFormExtensionContext.md) | LiveFormExtensionAbility组件上下文。 |

## AgentCard<sup>24+</sup>

type AgentCard = _AgentCard

[AgentCard](../apis-ability-kit/js-apis-inner-application-AgentCard.md)相当于Agent(智能体)的"名片"，用于描述Agent的能力和技能，由开发者在Agent的配置文件agent_config.json中配置。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentCard](../apis-ability-kit/js-apis-inner-application-AgentCard.md) | Agent(智能体)的"名片"，用于描述Agent的能力和技能。 |

## AgentProvider<sup>24+</sup>

type AgentProvider = _AgentProvider

[AgentProvider](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentprovider)表示Agent的服务提供商。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentProvider](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentprovider) | Agent的服务提供商。 |

## AgentCapabilities<sup>24+</sup>

type AgentCapabilities = _AgentCapabilities

[AgentCapabilities](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentcapabilities)用来定义Agent支持的可选能力。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentCapabilities](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentcapabilities) | 定义Agent支持的可选能力。 |

## AgentSkill<sup>24+</sup>

type AgentSkill = _AgentSkill

[AgentSkill](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentskill)表示Agent可以执行的不同能力或功能。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentSkill](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentskill) | 表示Agent可以执行的不同能力或功能。 |

## AgentAppInfo<sup>24+</sup>

type AgentAppInfo = _AgentAppInfo

[AgentAppInfo](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentappinfo)表示Agent所属的应用信息。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentAppInfo](../apis-ability-kit/js-apis-inner-application-AgentCard.md#agentappinfo) | Agent所属的应用信息。 |

## AgentHostProxy<sup>24+</sup>

type AgentHostProxy = _AgentHostProxy

[AgentHostProxy](../apis-ability-kit/js-apis-inner-application-agentHostProxy.md)用于从[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)服务端向客户端发送数据或安全认证请求。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentHostProxy](../apis-ability-kit/js-apis-inner-application-agentHostProxy.md) | 用于从[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)服务端向客户端发送数据或安全认证请求。 |

## AgentExtensionContext<sup>24+</sup>

type AgentExtensionContext = _AgentExtensionContext

[AgentExtensionContext](../apis-ability-kit/js-apis-inner-application-agentExtensionContext.md)是[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)的上下文环境，继承自[ExtensionContext](js-apis-inner-application-extensionContext.md)。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 类型 | 说明 |
| --- | --- |
| [_AgentExtensionContext](../apis-ability-kit/js-apis-inner-application-agentExtensionContext.md) | [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)的上下文环境，继承自[ExtensionContext](js-apis-inner-application-extensionContext.md)。 |

**示例：**

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
