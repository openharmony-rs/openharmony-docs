# setAppNet

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setAppNet

```TypeScript
function setAppNet(netHandle: NetHandle, callback: AsyncCallback<void>): void
```

将App绑定到特定的网络，绑定后App只能通过netHandle对应的网络访问网络。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | 是 | 网络句柄。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当成功绑定App到指定网络时，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
当应用绑定WIFI网络，WIFI弱信号或者断开时，如果不解绑，会导致应用无法上网。

以下示例以绑定WIFI网络为例，结合[on('netAvailable')](arkts-network-connection-netconnection-i.md#onnetavailable)、[on('netLost')](arkts-network-connection-netconnection-i.md#onnetlost)接口，当监听到WIFI网络可用时绑定WIFI网络，不可用时解绑，使用默认网络。
```


## setAppNet

```TypeScript
function setAppNet(netHandle: NetHandle): Promise<void>
```

将App异步绑定到特定的网络，绑定后App只能通过netHandle对应的网络访问网络。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | [NetHandle](arkts-network-connection-nethandle-i.md) | 是 | 网络句柄。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

参见 [setAppNet](#setappnet)
