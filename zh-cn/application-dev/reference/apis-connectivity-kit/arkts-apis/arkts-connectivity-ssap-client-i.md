# Client

SSAP客户端类，提供了和服务端进行连接和数据传输等操作方法。使用该类的方法前，需通过[ssap.createClient](arkts-connectivity-ssap-createclient-f.md)方法构造该类的实例。同一应用针对同一远端设备创建一个[Client](#client)实例即可，重复创建会增加不必要的资源开销。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## close

```TypeScript
close(): void
```

关闭客户端，断开与远端服务端的连接。如仅需断开当前连接而保留实例，请使用[disconnect](#disconnect)方法。

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

## connect

```TypeScript
connect(): Promise<void>
```

向服务端发起连接。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## disconnect

```TypeScript
disconnect(): Promise<void>
```

向服务端发起断连，断开已有连接或者终止正在建立的连接。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getServices

```TypeScript
getServices(): Promise<Service[]>
```

获取服务端支持的服务列表。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Service](arkts-connectivity-ssap-service-i.md)[]&gt; | Promise对象，返回服务端支持的服务列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
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

## offPropertyChange

```TypeScript
offPropertyChange(callback?: Callback<Property>): void
```

取消订阅属性变化事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Property](arkts-connectivity-ssap-property-i.md)&gt; | 否 | 回调函数，返回服务的Property。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

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

## onPropertyChange

```TypeScript
onPropertyChange(callback: Callback<Property>): void
```

订阅属性变化事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Property](arkts-connectivity-ssap-property-i.md)&gt; | 是 | 回调函数，返回服务的Property。 |

## readProperty

```TypeScript
readProperty(property: Property): Promise<Property>
```

读取服务端属性。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | 是 | 服务端属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Property](arkts-connectivity-ssap-property-i.md)&gt; | Promise对象，返回服务端属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## requestMtuSize

```TypeScript
requestMtuSize(mtu: number): Promise<void>
```

发起MTU协商请求。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mtu | number | 是 | MTU参数，取值范围[22, 1024]，单位：字节。默认值251。 单位为：字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## setPropertyNotification

```TypeScript
setPropertyNotification(property: Property, enable: boolean): Promise<void>
```

设置[Property](arkts-connectivity-ssap-property-i.md)变化通知。需在调用[connect](#connect)成功建立连接后使用。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | 是 | 服务端属性。该属性需支持NOTIFY操作（即operation包含NOTIFY，详见[Operation](arkts-connectivity-ssap-operation-e.md)）。 |
| enable | boolean | 是 | 是否打开通知功能。true: 打开通知功能。false: 关闭通知功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## writeProperty

```TypeScript
writeProperty(property: Property, writeType: PropertyWriteType): Promise<void>
```

写入服务端属性值。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | 是 | 服务端属性。 |
| writeType | [PropertyWriteType](arkts-connectivity-ssap-propertywritetype-e.md) | 是 | 写类型，支持服务端回复响应和不回复响应两种方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
