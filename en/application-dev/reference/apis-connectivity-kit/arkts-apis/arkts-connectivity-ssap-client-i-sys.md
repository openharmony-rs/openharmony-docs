# Client (System API)

```TypeScript
interface Client
```

Represents a SSAP client class. It provides APIs for connecting to and transmitting data with the server.

Before using the methods of this class, use the [ssap.createClient](arkts-connectivity-ssap-createclient-f.md) method to construct an instance of this class.

An app only needs to create one [Client](arkts-connectivity-ssap-client-i.md) instance for a remote device. Repeated creation will increase unnecessary resource overhead.

**Since:** 26.0.0

<!--Device-ssap-interface Client--><!--Device-ssap-interface Client-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## callMethod

```TypeScript
callMethod(method: Method): Promise<Method>
```

Describes the method for calling the server. For example, in a device control scenario, the client can call the configuration method provided by the server to remotely set device parameters or trigger specific operations. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-callMethod(method: Method): Promise<Method>--><!--Device-Client-callMethod(method: Method): Promise<Method>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| method | [Method](arkts-connectivity-ssap-method-i-sys.md) | Yes | Method for calling the server. The value must correspond to the method in the service on a remote device obtained during service discovery. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Method](arkts-connectivity-ssap-method-i-sys.md)&gt; | Promise used to return the **Method** object corresponding to the calling result. The **result** field is the return value after the server method is executed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getServicesByUuid

```TypeScript
getServicesByUuid(service: Service): Promise<Service[]>
```

Obtains a specified service supported by the server based on the service UUID. This API uses a promise to return the result.

Different from [getServices](arkts-connectivity-ssap-client-i.md#getservices), this API obtains only the service matching the specified UUID.

Only the **serviceUuid** field of the passed-in service is used to locate the target service on the server.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-getServicesByUuid(service: Service): Promise<Service[]>--><!--Device-Client-getServicesByUuid(service: Service): Promise<Service[]>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| service | [Service](arkts-connectivity-ssap-service-i.md) | Yes | Service to be obtained. Only the **serviceUuid** field is used to locate the target service. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Service](arkts-connectivity-ssap-service-i.md)[]&gt; | Promise used to return the result. The list contains the service matching the specified UUID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## offEventNotify

```TypeScript
offEventNotify(callback?: Callback<Event>): void
```

Unsubscribes from event notification events. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-offEventNotify(callback?: Callback<Event>): void--><!--Device-Client-offEventNotify(callback?: Callback<Event>): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**See also:** [onEventNotify](#oneventnotify) Subscribes to the event notification event.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Event](arkts-connectivity-ssap-event-i-sys.md)&gt; | No | Callback used to return the **Event** object of the service. <br>If this parameter is specified, the current callback is unregistered. If this parameter is not set, all callbacks corresponding to the type are unsubscribed. |

## onEventNotify

```TypeScript
onEventNotify(callback: Callback<Event>): void
```

Subscribes to event notification events. For example, in a device status monitoring scenario, the client subscribes to events to receive status change notifications (such as device alarms and data updates) pushed by the server in real time. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-onEventNotify(callback: Callback<Event>): void--><!--Device-Client-onEventNotify(callback: Callback<Event>): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**See also:** [offEventNotify](#offeventnotify) Unsubscribes from the event notification event.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Event](arkts-connectivity-ssap-event-i-sys.md)&gt; | Yes | Callback used to return the **Event** object of the service. |

## readDescriptor

```TypeScript
readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>
```

Reads a server descriptor. This API can be used only after a connection is established by calling [connect](arkts-connectivity-ssap-client-i.md#connect). This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>--><!--Device-Client-readDescriptor(descriptor: PropertyDescriptor): Promise<PropertyDescriptor>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | PropertyDescriptor | Yes | Server property descriptor. The value must correspond to the descriptor in the service on a remote device obtained during service discovery. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;PropertyDescriptor&gt; | Promise used to return the **PropertyDescriptor** object read from the server. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in descriptor. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## readPropertiesByUuid

```TypeScript
readPropertiesByUuid(property: Property): Promise<Property[]>
```

Reads server attributes based on the property UUID. This API uses a promise to return the result.

Different from [readProperty](arkts-connectivity-ssap-client-i.md#readproperty), which reads a single property, this API reads all properties matching the specified property UUID.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-readPropertiesByUuid(property: Property): Promise<Property[]>--><!--Device-Client-readPropertiesByUuid(property: Property): Promise<Property[]>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | Yes | Server attribute to read. The **propertyUuid** field specifies the property to read. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Property](arkts-connectivity-ssap-property-i.md)[]&gt; | Promise used to return the server attributes read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## setPropertyIndication

```TypeScript
setPropertyIndication(property: Property, enable: boolean): Promise<void>
```

Enables or disables indication for property value change. When the property value changes, the server proactively sends a notification to the client. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK and ohos.permission.MANAGE_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-setPropertyIndication(property: Property, enable: boolean): Promise<void>--><!--Device-Client-setPropertyIndication(property: Property, enable: boolean): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | Yes | Property from the server. |
| enable | boolean | Yes | Whether to enable indication for property value changes. **true**: enables indication. **false**: disables indication. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| 36100030 | The connection is not established. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## writeDescriptor

```TypeScript
writeDescriptor(descriptor: PropertyDescriptor): Promise<void>
```

Rewrites the server descriptor. This API uses a promise to return the result.

This API does not support writing the client property configuration descriptor (**CLIENT_PROPERTY_CONFIG**). To configure the client property notification or indication, use [setPropertyNotification](arkts-connectivity-ssap-client-i.md#setpropertynotification) or [setPropertyIndication](#setpropertyindication)

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Client-writeDescriptor(descriptor: PropertyDescriptor): Promise<void>--><!--Device-Client-writeDescriptor(descriptor: PropertyDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | PropertyDescriptor | Yes | Server property descriptor. The value must correspond to the descriptor in the service on a remote device obtained during service discovery. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in descriptor. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
