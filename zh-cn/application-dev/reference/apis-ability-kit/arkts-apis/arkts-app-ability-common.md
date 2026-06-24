# @ohos.app.ability.common

本模块提供Ability Kit中常用公共能力的纯类型定义，包含各类上下文对象、回调接口和数据结构。本模块仅导出类型声明，不包含具体实现逻辑或可执行代码。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityResult](arkts-ability-common-abilityresult-t.md) | 定义Ability被拉起并退出后返回的结果码和数据。<br/> |
| [AbilityStageContext](arkts-ability-common-abilitystagecontext-t.md) | [AbilityStage](arkts-ability-abilitystage-c.md#AbilityStage)组件上下文，继承自Context。<br/> |
| [AbilityStartCallback](arkts-ability-common-abilitystartcallback-t.md) | 定义了拉起UIExtensionAbility的回调结果，通常作为<br/>[UIAbilityContext.startAbilityByType](./application/UIAbilityContext:UIAbilityContext.startAbilityByType(type: string, wantParam: Record&lt;string, Object&gt;, abilityStartCallback: AbilityStartCallback, callback: AsyncCallback&lt;void&gt;))<br/>/<br/>[UIExtensionContext.startAbilityByType](@ohos.app.ability.UIExtensionContentSession:UIExtensionContentSession.startAbilityByType(type: string, wantParam: Record&lt;string, Object&gt;, abilityStartCallback: AbilityStartCallback, callback: AsyncCallback&lt;void&gt;))<br/>的入参传入。<br/> |
| [AgentAppInfo](arkts-ability-common-agentappinfo-t.md) | agent的应用程序相关信息。<br/> |
| [AgentCapabilities](arkts-ability-common-agentcapabilities-t.md) | AgentCard中的功能表示特定的skills、服务和功能<br/>agent可以在系统内执行或提供。<br/> |
| [AgentCard](arkts-ability-common-agentcard-t.md) | AgentCard在系统中显示agent的配置文件和联系信息。<br/> |
| <!--DelRow-->[AgentExtensionConnectCallback](arkts-ability-common-agentextensionconnectcallback-t-sys.md) | 表示AgentExtensionConnectCallback类型。<br/> |
| [AgentExtensionContext](arkts-ability-common-agentextensioncontext-t.md) | agent service ability的上下文。<br/> |
| [AgentHostProxy](arkts-ability-common-agenthostproxy-t.md) | AgentHostProxy是连接到Agent的客户端的代理对象，通过它可以与agent.的连接对应方通信。<br/> |
| [AgentProvider](arkts-ability-common-agentprovider-t.md) | AgentCard中的Provider是指发行和的组织或平台。<br/>管理代理的凭据。<br/> |
| <!--DelRow-->[AgentProxy](arkts-ability-common-agentproxy-t-sys.md) | 表示AgentProxy类型。<br/> |
| [AgentSkill](arkts-ability-common-agentskill-t.md) | AgentCard中的技能表示特定的 skills、专业知识和熟练程度<br/>用于执行任务或解决问题的代理。<br/> |
| [AppServiceExtensionContext](arkts-ability-common-appserviceextensioncontext-t.md) | [AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)<br/>组件上下文，继承自Context。<br/> |
| [ApplicationContext](arkts-ability-common-applicationcontext-t.md) | 应用上下文，继承自Context。<br/> |
| <!--DelRow-->[AutoFillExtensionContext](arkts-ability-common-autofillextensioncontext-t-sys.md) | AutoFillExtensionContext二级模块。<br/> |
| <!--DelRow-->[AutoStartupCallback](arkts-ability-common-autostartupcallback-t-sys.md) | AutoStartupCallback二级模块。<br/> |
| <!--DelRow-->[AutoStartupInfo](arkts-ability-common-autostartupinfo-t-sys.md) | AutoStartupInfo二级模块。<br/> |
| [BaseContext](arkts-ability-common-basecontext-t.md) | 所有Context类型的父类。<br/> |
| [ConnectOptions](arkts-ability-common-connectoptions-t.md) | 在连接指定的后台服务时作为入参，用于接收与后台服务的连接状态。<br/> |
| [Context](arkts-ability-common-context-t.md) | [Stage模型](../../../../application-models/ability-terminology.md#stage模型)的上下文基类。<br/> |
| [EmbeddableUIAbilityContext](arkts-ability-common-embeddableuiabilitycontext-t.md) | [EmbeddableUIAbility](arkts-ability-embeddableuiability-c.md#EmbeddableUIAbility)组件上下文，继承自Context。<br/> |
| [EventHub](arkts-ability-common-eventhub-t.md) | EventHub是系统提供的基于发布-订阅模式实现的事件通信机制。<br/> |
| [ExtensionContext](arkts-ability-common-extensioncontext-t.md) | [ExtensionAbility](arkts-ability-extensionability-c.md#ExtensionAbility)组件上下文，继承自Context。<br/> |
| [FormEditExtensionContext](arkts-ability-common-formeditextensioncontext-t.md) | The context of form edit extension. It allows access to<br/>formEditExtension-specific resources. |
| [FormExtensionContext](arkts-ability-common-formextensioncontext-t.md) | The context of form extension. It allows access to<br/>formExtension-specific resources.<br/> |
| [LiveFormExtensionContext](arkts-ability-common-liveformextensioncontext-t.md) | The context of live form extension. It allows access to<br/>liveFormExtension-specific resources.<br/> |
| [PacMap](arkts-ability-common-pacmap-t.md) | 存储基础数据类型的容器。<br/> |
| [PhotoEditorExtensionContext](arkts-ability-common-photoeditorextensioncontext-t.md) | The context of an photo editor extension ability.<br/> |
| <!--DelRow-->[ServiceExtensionContext](arkts-ability-common-serviceextensioncontext-t-sys.md) | ServiceExtensionContext二级模块。<br/> |
| [UIAbilityContext](arkts-ability-common-uiabilitycontext-t.md) | [UIAbility](arkts-app-ability-uiability.md)组件上下文，继承自Context。<br/> |
| [UIExtensionContext](arkts-ability-common-uiextensioncontext-t.md) | [UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)组件上下文，继承自Context。<br/> |
| [UIServiceExtensionConnectCallback](arkts-ability-common-uiserviceextensionconnectcallback-t.md) | 在连接指定的UIServiceExtensionAbility服务时作为入参，用于提供UIServiceExtensionAbility连接回调数据能力。<br/> |
| <!--DelRow-->[UIServiceExtensionContext](arkts-ability-common-uiserviceextensioncontext-t-sys.md) | UIServiceExtensionContext二级模块。<br/> |
| <!--DelRow-->[UIServiceHostProxy](arkts-ability-common-uiservicehostproxy-t-sys.md) | UIServiceHostProxy二级模块。<br/> |
| [UIServiceProxy](arkts-ability-common-uiserviceproxy-t.md) | UIServiceProxy提供了与UIServiceExtensionAbility服务端数据通信的能力。UIServiceExtensionAbility是一类特殊的ExtensionAbility组件，这类组件由系统提供，通<br/>常用于提供浮窗组件相关扩展能力。<br/> |
| [VpnExtensionContext](arkts-ability-common-vpnextensioncontext-t.md) | The context of vpn extension. It allows access to<br/>vpnExtension-specific resources.<br/>The class of auto startup info.<br/> |

