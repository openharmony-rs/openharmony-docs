# Client

SSAP客户端类，提供了和服务端进行连接和数据传输等操作方法。使用该类的方法前，需通过[ssap.createClient](arkts-connectivity-ssap-createclient-f.md)方法构造该类的实例。同一应用针对同一远端设备创建一个[Client](arkts-connectivity-ssap-client-i.md)实例即可，重复创建会增加不必要的资源开销。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## callMethod

```TypeScript
callMethod(method: Method): Promise<Method>
```

调用服务端方法。例如，在设备控制场景中，客户端可调用服务端提供的配置方法来远程设置设备参数或触发特定操作。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| method | [Method](arkts-connectivity-ssap-method-i-sys.md) | 是 | 服务端方法。需与服务发现时获取的对端Service中的method对应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Method](arkts-connectivity-ssap-method-i-sys.md)&gt; | Promise对象，返回调用结果对应的Method对象，其中result字段为服务端方法执行后的返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## offEventNotify

```TypeScript
offEventNotify(callback?: Callback<Event>): void
```

取消订阅事件通知事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Event&gt; | 否 | 回调函数，返回服务的事件对象。 填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

## onEventNotify

```TypeScript
onEventNotify(callback: Callback<Event>): void
```

订阅事件通知事件。例如，在设备状态监控场景中，客户端通过订阅事件来实时接收服务端推送的状态变化通知（如设备告警、数据更新等）。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Event&gt; | 是 | 回调函数，返回服务的事件对象。 |

## readDescriptor

```TypeScript
readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>
```

读取服务端描述符。需在调用[connect](arkts-connectivity-ssap-client-i.md#connect)建立连接成功后使用，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | PropertyDescriptor | 是 | 服务端属性描述符。需与服务发现时获取的对端Service中的descriptor对应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;PropertyDescriptor & gt; | Promise对象，返回从服务端读取到的属性描述符对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in descriptor. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## setPropertyIndication

```TypeScript
setPropertyIndication(property: Property, enable: boolean): Promise<void>
```

启用或禁用服务端属性值更改时的指示（当属性值发生变化时，服务端主动向客户端发送通知）。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | 是 | 服务端属性。 |
| enable | boolean | 是 | 是否启用属性值更改指示。true：启用指示。false：禁用指示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| 36100030 | The connection is not established. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## writeDescriptor

```TypeScript
writeDescriptor(descriptor: PropertyDescriptor): Promise<void>
```

改写服务端的描述符。使用Promise异步回调。

> **说明：**
> 
> 此接口不支持写入客户端属性配置描述符（CLIENT_PROPERTY_CONFIG），如需配置客户端属性通知或指示，请使用
> [setPropertyNotification](arkts-connectivity-ssap-client-i.md#setpropertynotification)或
> [setPropertyIndication](#setpropertyindication)。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | PropertyDescriptor | 是 | 服务端属性描述符。需与服务发现时获取的对端Service中的descriptor对应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in descriptor. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
