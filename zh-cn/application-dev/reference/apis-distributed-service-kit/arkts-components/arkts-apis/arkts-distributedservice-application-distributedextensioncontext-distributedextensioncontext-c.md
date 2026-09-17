# DistributedExtensionContext

用于分布式扩展功能的实现。

**继承/实现关系：** DistributedExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 20

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { DistributedExtensionContext } from '@kit.DistributedServiceKit';
```

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

将当前DistributedExtensionAbility连接到远端（其他设备上的）ServiceExtensionAbility，建立连接后通过onConnect回调返回的[rpc.IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md)代理与远端ServiceExtensionAbility进行跨设备IPC通信，以使用其对外提供的能力。适用于多设备限定协同场景，例如在当前设备上调用其他设备的后台服务能力。使用时，开发者首先通过Want中的deviceId指定目标设备、bundleName和abilityName指定目标ServiceExtensionAbility，并构造[ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md)实现onConnect、onDisconnect、onFailed三个回调分别处理连接成功、连接断开和连接失败状态；随后调用connectServiceExtensionAbility发起连接并获取返回的连接ID，连接成功后在onConnect回调中拿到IRemoteObject代理对象，基于该代理与远端ServiceExtensionAbility进行IPC通信；使用完毕后需调用[disconnectServiceExtensionAbility](#disconnectserviceextensionability)断开连接并释放资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 传入需要连接的远端ServiceExtensionAbility（服务扩展能力）的Want信息。系统将基于这些信息建立到远端设备的连接。 |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的配置对象，包含服务连接状态回调。连接成功时触发onConnect，连接断开时触发onDisconnect，连接失败时触发onFailed。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接ID，后续通过该ID断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
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
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

断开与远端ServiceExtensionAbility的连接，与[connectServiceExtensionAbility](#connectserviceextensionability)配对使用。调用connectServiceExtensionAbility后，必须在使用完毕后调用此方法释放连接资源，需要使用connectServiceExtensionAbility返回的连接ID调用此方法。断开连接之后开发者需要将连接成功时onConnect回调中返回的remote对象置空，以避免后续误用已失效的代理对象。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 连接ID，必须使用connectServiceExtensionAbility返回的连接ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000003](../../apis-ability-kit/errorcode-ability.md#16000003-指定的id不存在) | The connection id does not exist. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The ability has been destroyed. The context is no longer valid, meaning the context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
