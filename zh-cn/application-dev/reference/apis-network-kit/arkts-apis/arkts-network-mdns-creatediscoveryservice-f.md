# createDiscoveryService

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## createDiscoveryService

```TypeScript
function createDiscoveryService(context: Context, serviceType: string): DiscoveryService
```

返回一个DiscoveryService对象，该对象用于发现指定服务类型（serviceType）的MDNS服务。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-mdns-function createDiscoveryService(context: Context, serviceType: string): DiscoveryService--><!--Device-mdns-function createDiscoveryService(context: Context, serviceType: string): DiscoveryService-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 应用的上下文。 <br>FA模型的应用Context定义见Context。 <br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| serviceType | string | 是 | 需要发现的MDNS服务类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DiscoveryService](arkts-network-mdns-discoveryservice-i.md) | 基于指定服务类型（serviceType）和Context的发现服务对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

Stage模型示例：

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 获取context。
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

let serviceType = "_print._tcp";
let discoveryService : Object = mdns.createDiscoveryService(context, serviceType);
```

