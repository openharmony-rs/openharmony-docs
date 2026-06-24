# AppServiceExtensionContext

AppServiceExtensionContext模块是
[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)的
上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)。

AppServiceExtensionContext提供了连接、断开ServiceExtensionAbility（系统应用后台服务扩展组件）的能力，以及AppServiceExtensionAbility终止自身的能力。这里的
ServiceExtensionAbility只能由系统应用开发，支持三方应用连接。

> **说明：**
>
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** AppServiceExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

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
| number | 返回连接id，客户端可以通过<br/>[disconnectServiceExtensionAbility](arkts-na-appserviceextensioncontext-c.md#disconnectServiceExtensionAbility-1)传入该连接id来<br/>断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

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
| connection | number | 是 | 在<br/>[connectServiceExtensionAbility](arkts-na-appserviceextensioncontext-c.md#connectServiceExtensionAbility-1)中返回的连接id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

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
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported. |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid. |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid. |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit. |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported. |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified. |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported. |

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
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

