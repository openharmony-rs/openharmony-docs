# LiveFormExtensionContext

LiveFormExtensionContext是[LiveFormExtensionAbility](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md)的上下文，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。它提供访问特定于LiveFormExtensionAbility资源的能力，支持在互动卡片中拉起应用页面，适用 于需要在互动卡片中响应用户点击并跳转到应用页面的场景，解决了互动卡片无法主动拉起应用页面的限制问题。

**继承/实现关系：** LiveFormExtensionContext extends ExtensionContext

**起始版本：** 23

<!--Device-unnamed-declare class LiveFormExtensionContext--><!--Device-unnamed-declare class LiveFormExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

## connectServiceExtensionAbility

```TypeScript
public connectServiceExtensionAbility(want: Want, connection: ConnectOptions): long
```

将当前LiveFormExtensionAbility客户端连接到一个 [ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)服务端。 调用该接口前，必须实现ConnectOptions接口。 通过本接口连接成功后，LiveFormExtensionAbility可以通过ConnectOptions返回的[IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md)与 ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。 ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../application-models/extensionability-overview.md)组件，这类组件由系 统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。 ServiceExtensionAbility提供后台服务扩展能力，支持后台运行并对外提供相应能力。三方应用可以连接该ExtensionAbility，并进行通信。 通过本接口连接成功后，会启动ServiceExtensionAbility组件，具体请参考[组件启动规则](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiveFormExtensionContext-public connectServiceExtensionAbility(want: Want, connection: ConnectOptions): long--><!--Device-LiveFormExtensionContext-public connectServiceExtensionAbility(want: Want, connection: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称、Bundle名称等。 |
| connection | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息，连接成功会返回 [IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md)实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回连接id，客户端可以通过 [disconnectServiceExtensionAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form can not support this operation |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

## disconnectServiceExtensionAbility

```TypeScript
public disconnectServiceExtensionAbility(connectionId: long): Promise<void>
```

断开与[ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)的连接，断开连接之后开发者需要将连接成功时返回的 IRemoteObject对象置空。使用Promise异步回调。 ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../application-models/extensionability-overview.md)组件，这类组件由系 统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility提供后台服务扩展能力，支持后台运行并对外提供相应能力。三方应用可以连接该ExtensionAbility，并进行通信。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiveFormExtensionContext-public disconnectServiceExtensionAbility(connectionId: long): Promise<void>--><!--Device-LiveFormExtensionContext-public disconnectServiceExtensionAbility(connectionId: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connectionId | long | 是 | 连接的ServiceExtensionAbility的连接id，即 [connectServiceExtensionAbility](#connectserviceextensionability)返回的connectionId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form can not support this operation |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

