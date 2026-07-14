# @ohos.app.ability.common

本模块提供Ability Kit中常用公共能力的纯类型定义，包含各类上下文对象、回调接口和数据结构。本模块仅导出类型声明，不包含具体实现逻辑或可执行代码。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityResult](arkts-ability-abilityresult-t.md) | 定义Ability被拉起并退出后返回的结果码和数据。 |
| [AbilityStageContext](arkts-ability-abilitystagecontext-t.md) | [AbilityStage](arkts-ability-abilitystage-c.md)组件上下文，继承自Context。 |
| [AbilityStartCallback](arkts-ability-abilitystartcallback-t.md) | 定义了拉起UIExtensionAbility的回调结果，通常作为[UIAbilityContext.startAbilityByType](arkts-ability-uiabilitycontext-c.md#startabilitybytype-1)/[UIExtensionContext.startAbilityByType](arkts-ability-uiextensioncontentsession-c.md#startabilitybytype-1)的入参传入。 |
| [AgentAppInfo](arkts-ability-agentappinfo-t.md) | agent的应用程序相关信息。 |
| [AgentCapabilities](arkts-ability-agentcapabilities-t.md) | AgentCard中的功能表示特定的skills、服务和功能agent可以在系统内执行或提供。 |
| [AgentCard](arkts-ability-agentcard-t.md) | AgentCard在系统中显示agent的配置文件和联系信息。 |
| [AgentExtensionContext](arkts-ability-agentextensioncontext-t.md) | agent service ability的上下文。 |
| [AgentHostProxy](arkts-ability-agenthostproxy-t.md) | AgentHostProxy是连接到Agent的客户端的代理对象，通过它可以与agent.的连接对应方通信。 |
| [AgentProvider](arkts-ability-agentprovider-t.md) | AgentCard中的Provider是指发行和的组织或平台。管理代理的凭据。 |
| [AgentSkill](arkts-ability-agentskill-t.md) | AgentCard中的技能表示特定的 skills、专业知识和熟练程度用于执行任务或解决问题的代理。 |
| [AppServiceExtensionContext](arkts-ability-appserviceextensioncontext-t.md) | [AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)组件上下文，继承自Context。 |
| [ApplicationContext](arkts-ability-applicationcontext-t.md) | 应用上下文，继承自Context。 |
| [BaseContext](arkts-ability-basecontext-t.md) | 所有Context类型的父类。 |
| [ConnectOptions](arkts-ability-connectoptions-t.md) | 在连接指定的后台服务时作为入参，用于接收与后台服务的连接状态。 |
| [Context](arkts-ability-context-t.md) | [Stage模型](../../../../application-models/ability-terminology.md#stage模型)的上下文基类。 |
| [EmbeddableUIAbilityContext](arkts-ability-embeddableuiabilitycontext-t.md) | [EmbeddableUIAbility](arkts-ability-embeddableuiability-c.md)组件上下文，继承自Context。 |
| [EventHub](arkts-ability-eventhub-t.md) | EventHub是系统提供的基于发布-订阅模式实现的事件通信机制。 |
| [ExtensionContext](arkts-ability-extensioncontext-t.md) | [ExtensionAbility](arkts-ability-extensionability-c.md)组件上下文，继承自Context。 |
| [FormEditExtensionContext](arkts-ability-formeditextensioncontext-t.md) | The context of form edit extension. It allows access toformEditExtension-specific resources. |
| [FormExtensionContext](arkts-ability-formextensioncontext-t.md) | The context of form extension. It allows access toformExtension-specific resources. |
| [LiveFormExtensionContext](arkts-ability-liveformextensioncontext-t.md) | The context of live form extension. It allows access toliveFormExtension-specific resources. |
| [PacMap](arkts-ability-pacmap-t.md) | 存储基础数据类型的容器。 |
| [PhotoEditorExtensionContext](arkts-ability-photoeditorextensioncontext-t.md) | The context of an photo editor extension ability. |
| [UIAbilityContext](arkts-ability-uiabilitycontext-t.md) | [UIAbility](arkts-app-ability-uiability.md)组件上下文，继承自Context。 |
| [UIExtensionContext](arkts-ability-uiextensioncontext-t.md) | [UIExtensionAbility](arkts-ability-uiextensionability-c.md)组件上下文，继承自Context。 |
| [UIServiceExtensionConnectCallback](arkts-ability-uiserviceextensionconnectcallback-t.md) | 在连接指定的UIServiceExtensionAbility服务时作为入参，用于提供UIServiceExtensionAbility连接回调数据能力。 |
| [UIServiceProxy](arkts-ability-uiserviceproxy-t.md) | UIServiceProxy提供了与UIServiceExtensionAbility服务端数据通信的能力。UIServiceExtensionAbility是一类特殊的ExtensionAbility组件，这类组件由系统提供，通常用于提供浮窗组件相关扩展能力。 |
| [VpnExtensionContext](arkts-ability-vpnextensioncontext-t.md) | The context of vpn extension. It allows access tovpnExtension-specific resources.The class of auto startup info. |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AgentExtensionConnectCallback](arkts-ability-agentextensionconnectcallback-t-sys.md) | 表示AgentExtensionConnectCallback类型。 |
| [AgentProxy](arkts-ability-agentproxy-t-sys.md) | 表示AgentProxy类型。 |
| [AutoFillExtensionContext](arkts-ability-autofillextensioncontext-t-sys.md) | AutoFillExtensionContext二级模块。 |
| [AutoStartupCallback](arkts-ability-autostartupcallback-t-sys.md) | AutoStartupCallback二级模块。 |
| [AutoStartupInfo](arkts-ability-autostartupinfo-t-sys.md) | AutoStartupInfo二级模块。 |
| [ServiceExtensionContext](arkts-ability-serviceextensioncontext-t-sys.md) | ServiceExtensionContext二级模块。 |
| [UIServiceExtensionContext](arkts-ability-uiserviceextensioncontext-t-sys.md) | UIServiceExtensionContext二级模块。 |
| [UIServiceHostProxy](arkts-ability-uiservicehostproxy-t-sys.md) | UIServiceHostProxy二级模块。 |
<!--DelEnd-->

