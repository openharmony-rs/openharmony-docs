# removeLocalService

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## removeLocalService

```TypeScript
function removeLocalService(context: Context, serviceInfo: LocalServiceInfo,
                              callback: AsyncCallback<LocalServiceInfo>): void
```

移除一个MDNS服务，使用callback方式作为异步方法。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-mdns-function removeLocalService(context: Context, serviceInfo: LocalServiceInfo,                              callback: AsyncCallback<LocalServiceInfo>): void--><!--Device-mdns-function removeLocalService(context: Context, serviceInfo: LocalServiceInfo,                              callback: AsyncCallback<LocalServiceInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 应用的上下文。 <br>FA模型的应用Context定义见Context。 <br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| serviceInfo | [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | 是 | MDNS服务的信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 是 | Callback used to return the result. If the operation is successful, **error** is **undefined** and **data** is the MDNS服务的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2204002](../errorcode-net-mdns.md#2204002-未找到目标服务) | Callback not found. |
| [2204008](../errorcode-net-mdns.md#2204008-删除服务失败) | Failed to delete the service instance. |
| [2204010](../errorcode-net-mdns.md#2204010-发送消息失败) | Failed to send the message. |

**示例**

Stage模型示例：

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 获取context。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

let localServiceInfo: mdns.LocalServiceInfo = {
  serviceType: "_print._tcp",
  serviceName: "servicename",
  port: 5555,
  host: {
  address: "10.14.**.***",
  },
  serviceAttribute: [{key: "111", value: [1]}]
}

mdns.removeLocalService(context, localServiceInfo, (error: BusinessError, data: mdns.LocalServiceInfo) =>  {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## removeLocalService

```TypeScript
function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise<LocalServiceInfo>
```

移除一个MDNS服务，使用Promise方式作为异步方法。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-mdns-function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise<LocalServiceInfo>--><!--Device-mdns-function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise<LocalServiceInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 应用的上下文。 <br>FA模型的应用Context定义见Context。 <br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| serviceInfo | [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | 是 | MDNS服务的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | 以Promise形式返回移除的MDNS服务信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2204002](../errorcode-net-mdns.md#2204002-未找到目标服务) | Callback not found. |
| [2204008](../errorcode-net-mdns.md#2204008-删除服务失败) | Failed to delete the service instance. |
| [2204010](../errorcode-net-mdns.md#2204010-发送消息失败) | Failed to send the message. |

**示例**

Stage模型示例：

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

let localServiceInfo: mdns.LocalServiceInfo = {
  serviceType: "_print._tcp",
  serviceName: "servicename",
  port: 5555,
  host: {
  address: "10.14.**.***",
  },
  serviceAttribute: [{key: "111", value: [1]}]
}

mdns.removeLocalService(context, localServiceInfo).then((data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});
```

