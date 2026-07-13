# AppServiceExtensionContext

AppServiceExtensionContext模块是
[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)的
上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

AppServiceExtensionContext提供了连接、断开ServiceExtensionAbility（系统应用后台服务扩展组件）的能力，以及AppServiceExtensionAbility终止自身的能力。这里的
ServiceExtensionAbility只能由系统应用开发，支持三方应用连接。

> **说明：**
>
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** AppServiceExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, callback: ConnectOptions): number
```

将当前AppServiceExtensionAbility连接到一个ServiceExtensionAbility，通过返回的proxy与ServiceExtensionAbility进行通信，以使用
ServiceExtensionAbility对外提供的能力。仅支持在主线程调用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | Want类型参数，传入需要连接的Ability的信息，如Ability名称，Bundle名称等。 |
| callback | ConnectOptions | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接id，客户端可以通过[disconnectServiceExtensionAbility](arkts-na-appserviceextensioncontext-c.md#disconnectserviceextensionability-1)传入该连接id来断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

将AppServiceExtensionAbility与已连接的ServiceExtensionAbility断开连接。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 在[connectServiceExtensionAbility](arkts-na-appserviceextensioncontext-c.md#connectserviceextensionability-1)中返回的连接id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动UIAbility。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称、Bundle名称等。 |
| options | StartOptions | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported. |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid. |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit. |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported. |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported. |

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁AppServiceExtensionAbility自身。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

