# Server

SSAP服务端类，提供了和客户端进行连接和数据交互等操作方法。使用该类的方法前，需通过[ssap.createServer](arkts-connectivity-ssap-createserver-f.md)方法构造该类的实例。同一应用创建一个[Server](#server)实例即可，重复创建会增加不必要的资源开销。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## addService

```TypeScript
addService(service: Service): void
```

服务端添加服务。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| service | [Service](arkts-connectivity-ssap-service-i.md) | 是 | 服务端提供的服务信息，支持添加多个服务，根据不同的UUID区分。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## close

```TypeScript
close(): void
```

关闭服务端，并注销已注册的回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## notifyPropertyChanged

```TypeScript
notifyPropertyChanged(address: string, property: Property): Promise<void>
```

通知客户端属性值更新。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 客户端设备地址。地址格式参考：11:22:33:AA:BB:FF。 |
| property | [Property](arkts-connectivity-ssap-property-i.md) | 是 | 发生值变化的Property。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-无效地址) | Invalid address. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## offConnectionStateChange

```TypeScript
offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void
```

取消订阅连接状态变化事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)&gt; | 否 | 回调函数，返回连接状态上报参数。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

## offMtuChange

```TypeScript
offMtuChange(callback?: Callback<number>): void
```

取消订阅MTU变化事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数，返回协商后的MTU大小。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

## offPropertyRead

```TypeScript
offPropertyRead(callback?: Callback<PropertyReadRequest>): void
```

取消订阅客户端的读属性请求事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md)&gt; | 否 | 回调函数，返回客户端的Property读请求参数。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

## offPropertyWrite

```TypeScript
offPropertyWrite(callback?: Callback<PropertyWriteRequest>): void
```

取消订阅客户端的写属性请求事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md)&gt; | 否 | 回调函数，返回客户端的Property写请求参数。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

## onConnectionStateChange

```TypeScript
onConnectionStateChange(callback: Callback<ConnectionChangeState>): void
```

订阅连接状态变化事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)&gt; | 是 | 回调函数，返回连接状态上报参数。 |

## onMtuChange

```TypeScript
onMtuChange(callback: Callback<number>): void
```

订阅MTU变化事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数，返回协商后的MTU大小。 |

## onPropertyRead

```TypeScript
onPropertyRead(callback: Callback<PropertyReadRequest>): void
```

订阅客户端的读属性请求事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md)&gt; | 是 | 回调函数，返回客户端的Property读请求参数。 |

## onPropertyWrite

```TypeScript
onPropertyWrite(callback: Callback<PropertyWriteRequest>): void
```

订阅客户端的写属性请求事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md)&gt; | 是 | 回调函数，返回客户端的Property写请求参数。 |

## removeService

```TypeScript
removeService(serviceUuid: string): void
```

服务端删除服务。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceUuid | string | 是 | 星闪服务UUID，个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-00000000123 4，表示一个128位标识符。 不允许使用星闪标准UUID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## sendResponse

```TypeScript
sendResponse(response: ServerResponse): void
```

回复客户端读写请求。收到[ssap.onPropertyRead](#onpropertyread)或 [ssap.onPropertyWrite](#onpropertywrite)上报的请求后，调用本接口向对 应客户端回复数据。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | [ServerResponse](arkts-connectivity-ssap-serverresponse-i.md) | 是 | 回复客户端的响应数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-无效地址) | Invalid address. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
