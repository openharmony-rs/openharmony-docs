# UIServiceExtensionContext（系统接口）

UIServiceExtensionContext模块是[UIServiceExtension](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md)的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

UIServiceExtensionContext模块提供访问[UIServiceExtension](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md)特定资源以及具有的能力，包括启动、停止、绑定、解绑Ability。

> **说明：**  
>  
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** UIServiceExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 14

<!--Device-unnamed-declare class UIServiceExtensionContext extends ExtensionContext--><!--Device-unnamed-declare class UIServiceExtensionContext extends ExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

<a id="connectserviceextensionability"></a>
## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

连接到[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)，返回连接id。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceExtensionContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): long--><!--Device-UIServiceExtensionContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | Want parameter. |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-ability-connectoptions-t.md) | 是 | Connection options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Connection ID. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |

<a id="disconnectserviceextensionability"></a>
## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connectionId: number): Promise<void>
```

断开与[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)的连接，与[connectServiceExtensionAbility](arkts-na-uiserviceextensioncontext-c-sys.md#connectserviceextensionability-1)功能相反。使用Promise异步回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceExtensionContext-disconnectServiceExtensionAbility(connectionId: long): Promise<void>--><!--Device-UIServiceExtensionContext-disconnectServiceExtensionAbility(connectionId: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connectionId | number | 是 | 从[connectServiceExtensionAbility](arkts-na-uiserviceextensioncontext-c-sys.md#connectserviceextensionability-1)接口返回的连接Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

<a id="startability"></a>
## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动Ability。使用Promise异步回调。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>--><!--Device-UIServiceExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | Want类型参数，传入需要启动的ability的信息，如Ability名称，Bundle名称等。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

<a id="startabilitybytype"></a>
## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

按目标ability的类型启动[UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)或[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。仅支持处于前台的应用调用。使用Promise异步回调。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceExtensionContext-startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>--><!--Device-UIServiceExtensionContext-startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 目标ability类型。 |
| wantParam | Record&lt;string, Object&gt; | 是 | Want参数。 |
| abilityStartCallback | [AbilityStartCallback](../../apis-ability-kit/arkts-apis/arkts-ability-abilitystartcallback-i.md) | 是 | 拉起UIExtensionAbility执行结果的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

<a id="terminateself"></a>
## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁[UIServiceExtension](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md)。使用Promise异步回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceExtensionContext-terminateSelf(): Promise<void>--><!--Device-UIServiceExtensionContext-terminateSelf(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

