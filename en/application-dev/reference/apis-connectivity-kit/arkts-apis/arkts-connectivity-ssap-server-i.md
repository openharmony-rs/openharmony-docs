# Server

Represents a SSAP server class, which provides APIs for connecting to and exchanging data with the client.

Before using the methods of this class, you need to call [ssap.createServer](arkts-connectivity-ssap-createserver-f.md) to create an instance of this class.

An app only needs to create one [Server](arkts-connectivity-ssap-server-i.md) instance. Repeated creation will increase unnecessary resource overhead.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## addService

```TypeScript
addService(service: Service): void
```

Adds a service on the server.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| service | [Service](arkts-connectivity-ssap-service-i.md) | Yes | Service provided by the server. Multiple services can be added, identified by their UUIDs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## close

```TypeScript
close(): void
```

Closes the server and unregisters the callback.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## notifyPropertyChanged

```TypeScript
notifyPropertyChanged(address: string, property: Property): Promise<void>
```

Notifies the client of property value updates. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | string | Yes | Client device address. The address format is **11:22:33:AA:BB:FF**. |
| property | [Property](arkts-connectivity-ssap-property-i.md) | Yes | Property whose value changes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## offConnectionStateChange

```TypeScript
offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void
```

Unsubscribes from the connection status change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)&gt; | No | Callback used to return the connection status reporting parameters.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

## offMtuChange

```TypeScript
offMtuChange(callback?: Callback<number>): void
```

Unsubscribes from the MTU change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the MTU after negotiation.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

## offPropertyRead

```TypeScript
offPropertyRead(callback?: Callback<PropertyReadRequest>): void
```

Unsubscribes from the client property read request event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md)&gt; | No | Callback used to return the property read request parameters of the client.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

## offPropertyWrite

```TypeScript
offPropertyWrite(callback?: Callback<PropertyWriteRequest>): void
```

Unsubscribes from the client property write request event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md)&gt; | No | Callback used to return the property write request parameters of the client. If this parameter is specified, the current callback is unsubscribed. If this parameter is not specified, all callbacks corresponding to the event are unsubscribed. |

## onConnectionStateChange

```TypeScript
onConnectionStateChange(callback: Callback<ConnectionChangeState>): void
```

Subscribes to the connection status change event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)&gt; | Yes | Callback used to return the connection status reporting parameters. |

## onMtuChange

```TypeScript
onMtuChange(callback: Callback<number>): void
```

Subscribes to the MTU change event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the MTU after negotiation. |

## onPropertyRead

```TypeScript
onPropertyRead(callback: Callback<PropertyReadRequest>): void
```

Subscribes to the client property read request event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md)&gt; | Yes | Callback used to return the property read request parameters of the client. |

## onPropertyWrite

```TypeScript
onPropertyWrite(callback: Callback<PropertyWriteRequest>): void
```

Subscribes to the client property write request event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md)&gt; | Yes | Callback used to return the property write request parameters of the client. |

## removeService

```TypeScript
removeService(serviceUuid: string): void
```

Removes a service from the server.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceUuid | string | Yes | NearLink service UUID, which is a string of 36 characters. The value consists of 32 hexadecimal digits and four hyphens (-), for example, **FFFFFFFF-1234-5678-ABCD-000000001234**, which indicates a 128-bit ID. The value cannot be set to a standard NearLink UUID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## sendResponse

```TypeScript
sendResponse(response: ServerResponse): void
```

Responds to read or write requests from the client. After receiving a request reported by [ssap.onPropertyRead](#onpropertyread) or [ssap.onPropertyWrite](#onpropertywrite), call this API to send data to the corresponding client.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | [ServerResponse](arkts-connectivity-ssap-serverresponse-i.md) | Yes | Response data for the client. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-invalid-url) | Invalid address. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
