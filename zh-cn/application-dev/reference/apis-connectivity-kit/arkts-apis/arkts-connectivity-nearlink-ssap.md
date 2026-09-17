# @ohos.nearlink.ssap(星闪SSAP连接能力)

本模块提供了SSAP（星闪服务交互协议 SparkLink Service Access Protocol）连接功能，包括客户端创建与连接、调用服务端方法、读写描述符、订阅事件通知等。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createClient](arkts-connectivity-ssap-createclient-f.md) | 创建SSAP客户端实例。 |
| [createServer](arkts-connectivity-ssap-createserver-f.md) | 创建SSAP服务端实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | SSAP客户端类，提供了和服务端进行连接和数据传输等操作方法。 |
| [ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md) | 表示连接状态上报参数。 |
| [Property](arkts-connectivity-ssap-property-i.md) | 表示服务的Property。 |
| [PropertyDescriptor](arkts-connectivity-ssap-propertydescriptor-i.md) | 表示Property的描述符。 |
| [PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md) | 表示客户端的Property读请求参数。 |
| [PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md) | 表示客户端的Property写请求参数。 |
| [Server](arkts-connectivity-ssap-server-i.md) | SSAP服务端类，提供了和客户端进行连接和数据交互等操作方法。 |
| [ServerResponse](arkts-connectivity-ssap-serverresponse-i.md) | 表示回复客户端请求的响应。 |
| [Service](arkts-connectivity-ssap-service-i.md) | 表示星闪服务。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i-sys.md) | SSAP客户端类，提供了和服务端进行连接和数据传输等操作方法。 |
| [Event](arkts-connectivity-ssap-event-i-sys.md) | 表示服务的事件。 |
| [Method](arkts-connectivity-ssap-method-i-sys.md) | 表示服务的方法。 |
| [Service](arkts-connectivity-ssap-service-i-sys.md) | 表示星闪服务。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Operation](arkts-connectivity-ssap-operation-e.md) | 表示Property支持的操作类型，为枚举值。 |
| [PropertyDescriptorType](arkts-connectivity-ssap-propertydescriptortype-e.md) | 表示Property的描述符类型，为枚举值。 |
| [PropertyWriteType](arkts-connectivity-ssap-propertywritetype-e.md) | 表示Property支持的写类型，为枚举值。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ConnectionState](arkts-connectivity-ssap-connectionstate-t.md) | 表示和远端设备的连接状态，为枚举值。 |
