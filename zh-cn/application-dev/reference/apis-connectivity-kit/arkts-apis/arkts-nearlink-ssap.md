# @ohos.nearlink.ssap

提供操作或管理星闪服务的方法。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace ssap--><!--Device-unnamed-declare namespace ssap-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createClient](arkts-connectivity-ssap-createclient-f.md#createclient-1) | 创建SSAP客户端实例。 |
| [createServer](arkts-connectivity-ssap-createserver-f.md#createserver-1) | 创建SSAP服务端实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | 管理SSAP客户端。在调用ssap客户端方法之前，必须使用{@link createClient}创建ssap客户端实例。 |
| [ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md) | 描述SSAP连接状态。 |
| [Property](arkts-connectivity-ssap-property-i.md) | SSAP属性。 |
| [PropertyDescriptor](arkts-connectivity-ssap-propertydescriptor-i.md) | 属性的SSAP描述符。 |
| [PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md) | SSAP客户端属性读请求参数说明。 |
| [PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md) | SSAP客户端属性写请求参数说明。 |
| [Server](arkts-connectivity-ssap-server-i.md) | 管理SSAP服务端。在调用SSAP服务端方法之前，必须使用{@link createServer}创建SSAP服务端实例。 |
| [ServerResponse](arkts-connectivity-ssap-serverresponse-i.md) | 服务端对指定读或写请求的响应的参数。 |
| [Service](arkts-connectivity-ssap-service-i.md) | SSAP服务。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i-sys.md) | 管理SSAP客户端。在调用ssap客户端方法之前，必须使用{@link createClient}创建ssap客户端实例。 |
| [Event](arkts-connectivity-ssap-event-i-sys.md) | SSAP事件。 |
| [Method](arkts-connectivity-ssap-method-i-sys.md) | SSAP方法。 |
| [Service](arkts-connectivity-ssap-service-i-sys.md) | SSAP服务。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Operation](arkts-connectivity-ssap-operation-e.md) | 属性操作指示的枚举。 |
| [PropertyDescriptorType](arkts-connectivity-ssap-propertydescriptortype-e.md) | 属性描述符类型的枚举。 |
| [PropertyWriteType](arkts-connectivity-ssap-propertywritetype-e.md) | 属性写入类型的枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ConnectionState](arkts-connectivity-ssap-connectionstate-t.md) | 连接状态。 |

