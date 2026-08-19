# connectAgentExtensionAbility（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## connectAgentExtensionAbility

```TypeScript
function connectAgentExtensionAbility(want: Want, agentId: string,
    callback: AgentExtensionConnectCallback): Promise<AgentProxy>
```

将当前调用方组件连接到 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)。通过返回的 [AgentProxy](arkts-ability-agentproxy-i-sys.md)与 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)进行通信，以使用 AgentExtensionAbility对外提供的能力。 > **说明：** > > - 当目标Agent的AgentCard为 > LOW_CODE > 类型时，AgentExtensionAbility的 > [onConnect](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md#onconnect)只在此类Agent连接 > 成功时回调；后续连接的此类Agent，只回调 > [onAgentInvoked](arkts-ability-app-agent-agentextensionability-agentextensionability-c-sys.md#onagentinvoked)。 > > - 同一个AgentExtensionAbility中，最多只能同时运行100个LOW_CODE类型的Agent，否则会报35600003错误码。 > > - 同一个AgentExtensionAbility中，不允许重复连接同一个LOW_CODE类型的Agent。

**起始版本：** 24

**需要权限：** ohos.permission.CONNECT_AGENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-agentManager-function connectAgentExtensionAbility(want: Want, agentId: string,    callback: AgentExtensionConnectCallback): Promise<AgentProxy>--><!--Device-agentManager-function connectAgentExtensionAbility(want: Want, agentId: string,    callback: AgentExtensionConnectCallback): Promise<AgentProxy>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)所属的Want 信息，通常需要包括bundle名称、ability名称。 |
| agentId | string | 是 | [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)所属的 agentId。 |
| callback | [AgentExtensionConnectCallback](arkts-ability-agentextensionconnectcallback-i-sys.md) | 是 | 连接回调函数，包含接收 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)服务端的数据、 安全认证数据以及断开连接事件的回调接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AgentProxy](arkts-ability-agentproxy-i-sys.md)&gt; | Promise对象，返回的AgentProxy对象，用于从客户端向AgentExtensionAbility服务端发送数据或安全认证请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out.<br>**适用版本：** 26.0.0+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [35600007](../errorcode-ability.md#35600007-指定的low_code类型智能体已触发且尚未完成工作流) | The specified LOW_CODE agent is already active and is not yet completed.<br>**适用版本：** 26.0.0+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by enterprise device management (EDM). |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [35600003](../errorcode-ability.md#35600003-调用方已达到最大连接数) | Maximum connections from the same caller have been reached. Please disconnect at least one agent extension beforehand. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [35600001](../errorcode-ability.md#35600001-指定的agentid不存在) | The specified agentId does not exist. |

