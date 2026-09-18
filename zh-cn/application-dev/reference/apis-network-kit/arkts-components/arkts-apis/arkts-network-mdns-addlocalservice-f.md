# addLocalService

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## addLocalService

```TypeScript
function addLocalService(context: Context, serviceInfo: LocalServiceInfo,
                           callback: AsyncCallback<LocalServiceInfo>): void
```

添加一个MDNS服务，使用callback方式作为异步方法。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 应用的上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| serviceInfo | [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | 是 | mDNS服务的信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 是 | Callback used to return the result. If the operation is successful, **error** is **undefined** and **data** is the mDNS服务的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2204003](../errorcode-net-mdns.md#2204003-重复注册) | Callback duplicated. |
| [2204008](../errorcode-net-mdns.md#2204008-删除服务失败) | Failed to delete the service instance. |
| [2204010](../errorcode-net-mdns.md#2204010-发送消息失败) | Failed to send the message. |

**示例**

```TypeScript
> 说明：
> 
> 在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

Stage模型示例：
```


## addLocalService

```TypeScript
function addLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise<LocalServiceInfo>
```

添加一个MDNS服务，使用Promise方式作为异步方法。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 应用的上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| serviceInfo | [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | 是 | MDNS服务的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 以Promise形式返回添加的MDNS服务信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2204003](../errorcode-net-mdns.md#2204003-重复注册) | Callback duplicated. |
| [2204008](../errorcode-net-mdns.md#2204008-删除服务失败) | Failed to delete the service instance. |
| [2204010](../errorcode-net-mdns.md#2204010-发送消息失败) | Failed to send the message. |

**示例**

参见 [addLocalService](#addlocalservice)
