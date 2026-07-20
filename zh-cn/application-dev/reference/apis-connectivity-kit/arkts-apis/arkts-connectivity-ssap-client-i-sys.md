# Client

管理SSAP客户端。在调用ssap客户端方法之前，必须使用{@link createClient}创建ssap客户端实例。

**起始版本：** 26.0.0

<!--Device-ssap-interface Client--><!--Device-ssap-interface Client-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

<a id="callmethod"></a>
## callMethod

```TypeScript
callMethod(method: Method): Promise<Method>
```

调用服务端的方法。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-callMethod(method: Method): Promise<Method>--><!--Device-Client-callMethod(method: Method): Promise<Method>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| method | [Method](arkts-connectivity-ssap-method-i-sys.md) | 是 | 指示要调用的方法 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Method&gt; | Promise用于返回方法结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="offeventnotify"></a>
## offEventNotify

```TypeScript
offEventNotify(callback?: Callback<Event>): void
```

取消订阅事件通知。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-offEventNotify(callback?: Callback<Event>): void--><!--Device-Client-offEventNotify(callback?: Callback<Event>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Event&gt; | 否 | 用于监听事件通知事件的回调。 |

<a id="oneventnotify"></a>
## onEventNotify

```TypeScript
onEventNotify(callback: Callback<Event>): void
```

订阅事件通知。

只有授予了ohos.permission.NEARLINK_ACCESS权限的系统应用程序才能访问此事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-onEventNotify(callback: Callback<Event>): void--><!--Device-Client-onEventNotify(callback: Callback<Event>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Event&gt; | 是 | 用于监听事件通知事件的回调。 |

<a id="readdescriptor"></a>
## readDescriptor

```TypeScript
readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>
```

读取服务器的描述符。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>--><!--Device-Client-readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [PropertyDescriptor](arkts-connectivity-ssap-propertydescriptor-i.md) | 是 | 指示要读取的描述符 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PropertyDescriptor&gt; | Promise用于返回描述符值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink.md#36100043-无效uuid) | Invalid UUID in descriptor. |
| [36100044](../errorcode-nearlink.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="setpropertyindication"></a>
## setPropertyIndication

```TypeScript
setPropertyIndication(property: Property, enable: boolean): Promise<void>
```

启用或禁用属性值变更指示。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-setPropertyIndication(property: Property, enable: boolean): Promise<void>--><!--Device-Client-setPropertyIndication(property: Property, enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | 是 | 要指示的属性。 |
| enable | boolean | 是 | 指定是否启用属性的指示 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| 36100030 | The connection is not established. |
| [36100043](../errorcode-nearlink.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

<a id="writedescriptor"></a>
## writeDescriptor

```TypeScript
writeDescriptor(descriptor: PropertyDescriptor): Promise<void>
```

写入服务端的描述符。

此方法不支持写入客户端属性配置描述符。要写入客户端属性配置描述符，请改为调用[setPropertyNotification](arkts-connectivity-ssap-client-i.md#setpropertynotification-1)或[setPropertyIndication](arkts-connectivity-ssap-client-i-sys.md#setpropertyindication-1)。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-writeDescriptor(descriptor: PropertyDescriptor): Promise<void>--><!--Device-Client-writeDescriptor(descriptor: PropertyDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [PropertyDescriptor](arkts-connectivity-ssap-propertydescriptor-i.md) | 是 | 指示要写入的描述符。<br>描述符类型不应为CLIENT_PROPERTY_CONFIG。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise用于返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink.md#36100043-无效uuid) | Invalid UUID in descriptor. |
| [36100044](../errorcode-nearlink.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

